# OOP in C++ — Placement Prep Guide

## 1. The Four Pillars

| Pillar | What it means | C++ mechanism |
|---|---|---|
| Encapsulation | Bundling data + methods, hiding internal state | `class` with `private`/`protected` members, getters/setters |
| Abstraction | Exposing only relevant details | Abstract classes, pure virtual functions, interfaces |
| Inheritance | Reusing/extending behavior of another class | `class Derived : access Base` |
| Polymorphism | One interface, many implementations | Function overloading, operator overloading, virtual functions |

Interviewers love: **"Explain OOP pillars with a real-world example."** Have one ready (e.g., a `Vehicle` → `Car`/`Bike` hierarchy).

---

## 2. Classes & Objects — Fundamentals

```cpp
class Student {
private:
    string name;
    int marks;
public:
    Student(string n, int m) : name(n), marks(m) {}   // constructor, initializer list
    void display() const { cout << name << ": " << marks << endl; }
};
```

**Key points to remember:**
- `struct` vs `class`: only difference is default access — `public` for struct, `private` for class.
- Member initializer list vs assignment in constructor body: initializer list is more efficient (avoids default-construct-then-assign), and is **mandatory** for `const` members, references, and members without a default constructor.
- Objects can be created on stack (`Student s(...)`) or heap (`Student* s = new Student(...)`); heap objects must be `delete`d.

---

## 3. Constructors & Destructors

### Types of constructors
- **Default** — no arguments
- **Parameterized**
- **Copy constructor** — `Student(const Student &s)`
- **Move constructor** (C++11) — `Student(Student &&s) noexcept`

### Rule of Three / Five / Zero
If your class manages a resource (raw pointer, file handle), you generally need:
- **Rule of Three**: destructor, copy constructor, copy assignment operator
- **Rule of Five** (C++11+): add move constructor, move assignment operator
- **Rule of Zero**: prefer using smart pointers / STL containers so you don't need to write any of the above

### Shallow vs Deep Copy — classic interview question
```cpp
class Buffer {
    int* data;
public:
    Buffer(int size) { data = new int[size]; }
    // Shallow copy (default, compiler-generated) — both objects point to SAME memory -> double free bug
    // Deep copy (correct, user-defined):
    Buffer(const Buffer& other) {
        data = new int[/* size */];
        // copy actual values
    }
    ~Buffer() { delete[] data; }
};
```
**Be ready to explain**: why the default copy constructor is dangerous when a class holds raw pointers, and how it leads to double-free / dangling pointer bugs.

### Destructor order
- Constructors run **base → derived**; destructors run **derived → base** (reverse order).
- Destructors of members run in **reverse order of declaration**.

### Why destructors should be `virtual` in base classes
```cpp
class Base { public: virtual ~Base() {} };
```
If a `Base*` pointing to a `Derived` object is deleted without a virtual destructor, **only `Base`'s destructor runs** → resource leak / undefined behavior. Very common interview question.

---

## 4. Static Members

```cpp
class Counter {
    static int count;   // declaration
public:
    Counter() { count++; }
    static int getCount() { return count; }  // static member function
};
int Counter::count = 0;  // definition (outside class, must-know syntax)
```
- Shared across all objects, one copy per class (not per object).
- Static member functions can't access non-static members (no `this` pointer).

---

## 5. Inheritance

### Types
Single, Multiple, Multilevel, Hierarchical, Hybrid.

### Access specifiers in inheritance
| Base member | `public` inheritance | `protected` inheritance | `private` inheritance |
|---|---|---|---|
| public | public | protected | private |
| protected | protected | protected | private |
| private | inaccessible | inaccessible | inaccessible |

### The Diamond Problem (multiple inheritance)
```cpp
class A { public: int x; };
class B : public A {};
class C : public A {};
class D : public B, public C {};  // D has TWO copies of A::x -> ambiguous
```
**Fix — virtual inheritance:**
```cpp
class B : virtual public A {};
class C : virtual public A {};
class D : public B, public C {};  // only ONE copy of A now
```
This is a favorite whiteboard question — practice drawing it.

---

## 6. Polymorphism

### Compile-time (Static) Polymorphism
- **Function overloading** — same name, different signature
- **Operator overloading**
- Resolved at compile time; no runtime overhead

### Run-time (Dynamic) Polymorphism
- **Function overriding** using `virtual` functions
- Resolved via **vtable / vptr** at runtime

```cpp
class Shape {
public:
    virtual double area() const { return 0; }   // virtual function
    virtual ~Shape() {}
};
class Circle : public Shape {
    double r;
public:
    Circle(double radius) : r(radius) {}
    double area() const override { return 3.14159 * r * r; }  // 'override' keyword (C++11)
};

Shape* s = new Circle(5);
cout << s->area();   // calls Circle::area() -> dynamic dispatch
```

### How it works internally (frequently asked)
- Each class with virtual functions has a **vtable** (array of function pointers).
- Each object of such a class has a hidden **vptr** pointing to its class's vtable.
- Calling a virtual function = look up vptr → vtable → correct function. This is why virtual calls have a small runtime cost.

### Pure virtual functions & abstract classes
```cpp
class Shape {
public:
    virtual double area() const = 0;   // pure virtual -> makes Shape abstract
};
```
- Abstract classes cannot be instantiated.
- A derived class must override **all** pure virtual functions to become concrete.
- This is C++'s way of defining an "interface."

### Function Overloading vs Overriding (classic table question)
| | Overloading | Overriding |
|---|---|---|
| Binding | Compile-time | Runtime |
| Signature | Must differ | Must be same |
| Requires inheritance? | No | Yes |
| Keyword | — | `virtual` in base |

---

## 7. Operator Overloading

```cpp
class Complex {
    double re, im;
public:
    Complex(double r, double i) : re(r), im(i) {}
    Complex operator+(const Complex& other) const {
        return Complex(re + other.re, im + other.im);
    }
    friend ostream& operator<<(ostream& os, const Complex& c);
};
ostream& operator<<(ostream& os, const Complex& c) {
    os << c.re << " + " << c.im << "i";
    return os;
}
```
- Some operators **cannot** be overloaded: `::`, `.`, `.*`, `?:`, `sizeof`.
- `=`, `[]`, `()`, `->` must be overloaded as **member functions** (not free functions).

---

## 8. `this` Pointer, `friend`, and Access Control

- `this` is an implicit pointer to the calling object, available inside non-static member functions.
- `friend` functions/classes can access private/protected members but **break encapsulation** — know the tradeoff, interviewers may ask when it's justified (e.g., operator overloading needing symmetric access).

---

## 9. Templates (Generic Programming — often clubbed with OOP rounds)

```cpp
template <typename T>
class Stack {
    vector<T> data;
public:
    void push(T val) { data.push_back(val); }
    T pop() { T v = data.back(); data.pop_back(); return v; }
};
```
- Enables writing type-independent classes/functions.
- Templates are resolved at **compile time** (unlike Java generics which use type erasure).

---

## 10. Exception Handling

```cpp
try {
    if (x == 0) throw runtime_error("Division by zero");
} catch (const runtime_error& e) {
    cout << e.what();
} catch (...) {
    cout << "Unknown exception";
}
```
- Always catch exceptions **by reference** to avoid slicing.
- Custom exceptions: inherit from `std::exception` and override `what()`.

---

## 11. High-Frequency Interview Questions

1. What is the difference between compile-time and run-time polymorphism?
2. Why can't constructors be virtual, but destructors can/should be?
3. What happens if you don't mark a base class destructor `virtual`?
4. Explain the diamond problem and how virtual inheritance solves it.
5. What is object slicing? (Assigning a derived object to a base object by value truncates the derived part.)
6. Difference between deep copy and shallow copy — write code for both.
7. Can a constructor call a virtual function? (Yes, but it won't dispatch polymorphically — it calls the version for the currently-constructing class, since the vtable isn't fully set up yet.)
8. What is a pure virtual function? What is an abstract class? Can an abstract class have a constructor?
9. Difference between `struct` and `class` in C++.
10. What is the size of an empty class? (1 byte, to ensure distinct addresses.) What if it has a virtual function? (grows by pointer size, for the vptr.)
11. Static vs dynamic binding.
12. Why is multiple inheritance considered risky? How does C++ handle it vs Java (which disallows it, using interfaces instead)?
13. Difference between `override` and `final` (C++11 keywords).
14. Can you overload the assignment operator? Why is it important to check for self-assignment inside `operator=`?

---

## 12. Common Gotchas / Traps Interviewers Set

- **Slicing**: `Base b = derivedObj;` loses derived-class data — always use pointers/references for polymorphism.
- **Calling virtual functions in constructors/destructors** doesn't behave polymorphically.
- **Forgetting virtual destructor** → memory leak when deleting via base pointer.
- **Returning reference to local variable** inside a member function → dangling reference.
- **`const` correctness**: mark member functions `const` when they don't modify state; needed for calling them on `const` objects/references.

---

## Suggested Practice Flow
1. Write a small hierarchy (e.g., `Animal` → `Dog`, `Cat`) from scratch using virtual functions.
2. Implement Rule of Three manually on a class managing a raw array.
3. Trace through the diamond problem with and without `virtual` inheritance.
4. Practice explaining vtable/vptr on a whiteboard — this is asked very often at product-based companies.
