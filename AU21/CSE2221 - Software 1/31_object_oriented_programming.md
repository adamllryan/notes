An **object** is the idea of a class being an object, where we pretend that object is like an object in real life.
A **class** is a user-defined datatype that can be created and used by creating an instance of that class. Fundamental!!!!

# Inheritance
**Inheritance** is the concept of having classes inherit from classes or interfaces. It lets us create hierarchies of implementations and reuse code. 

# Polymorphism
**Polymorphism** is the idea of having many forms. It is the idea of overloading (static) or overriding (dynamic). 

**Static** polymorphism overloads when we write multiple methods with the same names but unique parameters and return types (must have different parameters, though). It can be checked at compile time. 

**Dynamic** polymorphism is when we override a method present in a superclass, letting us customize or replace that entire method. We can use keywords like @override and super() to do so. 

**Binding** is what the JVM chooses to run. If we have multiple overrides, the compiler will use the method of whatever class is implemented, not the class we reference. If we write something like "BaseClass c = new ChildClass();", the class "ChildClass" will always be called because it is of type ChildClass, not BaseClass. Polymorphism

# Abstraction
**Abstraction** is the concept of intent rather than implementation. This is the idea of using interfaces to create a skeleton of how we want our objects to function, which we later implement. The idea is that our classes should not understand how other classes work, just the abstract "interface" of what the methods are. This also means we need well-written method names and contracts. 
# Encapsulation
**Encapsulation** is the mechanism of hiding the implementation of data by restricting access to public methods. We create private variables that are only accessible outside the class by public get/set methods and methods we want to use to modify the values. A list in Java may just be an array but we have extra methods to manipulate that array like it were a list. Think NaturalNumber from the course project series. 



