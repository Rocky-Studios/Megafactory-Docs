# Object Oriented Programming

If you have never coded in a high-level language before, you will need to familiarize yourself with the two main types of programming: **statically typed** and **object oriented**.

Static, or statically typed code, is code that there is only one instance of. For example, the Logger class there is only once instance of; there is always only one logger than you use.

Objects, or object oriented code, is code that is collected under an object. Then you can make multiple instances of this object. For example, you can create a Dog object, then you can make 2 or 3 or more instances of that object, without having to copy and paste all the Dog code over and over again, because sometimes you have hundreds or even thousands of instances of the same object.

## Pillars of OOP
There are 4 'pillars' of OOP, which are all useful when working with objects and many instances of them. They are:

- **Encapsulation**

- **Inheritance**

- **Abstraction** and

- **Polymorphism**

### Encapsulation
Say you have a variable called `age` that belongs to an object 'Person'. That might look like this:
```cs
class Person
{
  int age;
}
```
Usually, if you want to make this variable accesible from other classes, you would make it public
```cs
public int Age;
```
which enables you to use it like this:
```cs
//Some other class
Person bob = new Person();
bob.age = 30;
Logger.Log(bob.age);
```

This is all well and good, but what if you tried to set the age to `-1` like `bob.age = -1;`? This is where encapsulation comes in handy. *Encapsulating* the `age` variable means making it private, and making two public methods for it, a getter and a setter.

!!! tip
    Notice how I've made the age variable start with an underscore (`_`). This is an ease-of-readibilty thing, and these are the rules (that I prefer) for naming variables:

    - public variables should start with a Capital letter, then go like this: `MyPublicVariable`

    - private variables should start with an underscore `_` followed by a lowercase letter, then go like this `_myPrivateVariable`
  
    **Note:** variables default to private.

```cs
private int _age;

public void SetAge(int age)
{
  _age = age;
}
public int GetAge()
{
  return _age;
}
```