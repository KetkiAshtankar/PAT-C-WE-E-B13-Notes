# 🐍 Python OOPs Concepts – Notes

## 1️⃣ Class → Blueprint

A **class** is a blueprint for creating objects.


```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model
```

---

## 2️⃣ Object → Instance of Class

An **object** is an actual instance created from a class.

```python
car1 = Car("Tesla", "Model S")
print(car1.brand)   # Tesla
```

---

## 3️⃣ Encapsulation → Data Hiding (`__privateVar`)

Encapsulation means **restricting access** to some data or methods.

```python
class Bank:
    def __init__(self):
        self.__balance = 1000   # private variable

    def deposit(self, amount):
        self.__balance += amount

    def get_balance(self):
        return self.__balance

acc = Bank()
acc.deposit(500)
print(acc.get_balance())   # 1500
```

---

## 4️⃣ Inheritance → Code Reuse (Parent → Child)

Inheritance allows a class to **reuse code** from another class.

```python
class Vehicle:
    def __init__(self, brand):
        self.brand = brand

class Car(Vehicle):
    def __init__(self, brand, model):
        super().__init__(brand)
        self.model = model

c = Car("Toyota", "Corolla")
print(c.brand, c.model)   # Toyota Corolla
```

---

## 5️⃣ Polymorphism → Same Method, Different Behavior

Polymorphism means **same method name, different implementations**.

```python
class Dog:
    def speak(self):
        return "Woof!"

class Cat:
    def speak(self):
        return "Meow!"

for animal in (Dog(), Cat()):
    print(animal.speak())
# Woof!
# Meow!
```

---

## 6️⃣ Abstraction → Hiding Implementation Details

Abstraction shows only the **essential features**, hiding internal logic.

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        return "Bark"

d = Dog()
print(d.sound())   # Bark
```

---

## 7️⃣ Constructor (`__init__`) → Initializes Object

Called automatically when object is created.

```python
class Student:
    def __init__(self, name):
        self.name = name

s = Student("Alice")
print(s.name)   # Alice
```

---

## 8️⃣ Destructor (`__del__`) → Cleans Up Object

Called automatically when object is deleted.

```python
class Demo:
    def __del__(self):
        print("Object destroyed!")

obj = Demo()
del obj   # Object destroyed!
```

---

## 9️⃣ `self` → Current Object Reference

Represents the current object inside the class.

```python
class Person:
    def __init__(self, name):
        self.name = name   # self refers to the instance

p = Person("John")
print(p.name)   # John
```

---

## 🔟 Static Method → No `self` or `cls`

Belongs to class, but doesn’t need object reference.

```python
class Math:
    @staticmethod
    def add(a, b):
        return a + b

print(Math.add(5, 3))   # 8
```

---

## 1️⃣1️⃣ Class Method → Works with `cls`

Class methods work on the **class itself**.

```python
class Student:
    count = 0

    def __init__(self):
        Student.count += 1

    @classmethod
    def get_count(cls):
        return cls.count

s1 = Student()
s2 = Student()
print(Student.get_count())   # 2
```

---

# ✅ Summary

* **Class** → Blueprint
* **Object** → Instance of class
* **Encapsulation** → Data hiding (`__privateVar`)
* **Inheritance** → Code reuse (Parent → Child)
* **Polymorphism** → Same method, different behavior
* **Abstraction** → Hide details, show only essentials
* **Constructor (`__init__`)** → Initializes object
* **Destructor (`__del__`)** → Cleans up object
* **self** → Current object reference
* **Static Method** → No `self`/`cls`
* **Class Method** → Works with `cls`

---
