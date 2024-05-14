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

#### Why is this useful?
This helps us prevent the problem we have before, assigning a negative number to an age. Encapsulation forces you to use the methods, which allows you to add checking before returning or assigning, like this:
```cs
public void SetAge(int age)
{
  if(age < 0) return;
  _age = age;
}
```

### Inheritance
Let's say you have a class called `Animal`:
```cs
public class Animal
{
  public string Name;
  private int _age;

  public void SetAge(int age)
  {
    if(age < 0) return;
    _age = age;
  }
  public int GetAge()
  {
    return _age;
  }
}
```

and you want another class called `Dog`. Dogs have some specific traits, for example a collar colour.
```cs
public class Dog
{
  public string Name;
  public string CollarColour;
  private int _age;

  public void SetAge(int age)
  {
    if(age < 0) return;
    _age = age;
  }
  public int GetAge()
  {
    return _age;
  }
}
```
Notice how the two classes have a lot of common code, like the name, age and the getter/setter methods. This is where we can make the `Dog` class inherit from the `Animal` class.

The animal class will stay the same, but the `Dog` class will change drastically:
```cs
class Dog: Animal
{
  public string collarColour;
}
```
The `:` character denotes inheritance; the `Dog` class is inheriting everything from the `Animal` class. This means we can use it like this:
```cs
// Some other code
Dog liam = new Dog();

liam.Name = "Liam";
liam.CollarColour = "Blue";
liam.SetAge(2);
```
#### Why is this useful?
This stops you from having to rewrite code, and also, when you change one of the methods in the parent class, it will automatically change for all the child classes.
!!! tip 
    Classes can only inherit from one other class, but an infinite amount of interfaces.

### Abstraction
An abstract class (or interface) is a class that cannot be used directly. The animal class is a good example of this.
```cs
abstract class Animal
{
  //...
}
```
This means that you cannot use the animal class, only its derivatives. You can't have an animal that is just *an animal*, it has to have a type, like a dog or a cat. Making the animal class abstract means the second line works but the first line throws an error.
```cs
//Cannot create an instance of the abstract class or interface 'Animal'
Animal tom = new Animal();

Dog tom = new Dog(); //Works
```
#### Why is this useful?
If you want to create a class that essentially works as a 'template'.

### Polymorphism
Going back to the `Animal` and `Dog` example, let's say you know that a Dog can only be a maximum of 20 years old. You can't modify the `SetAge` method in the `Animal` class, because then all the animals would have a max age of 20.
```cs
public void SetAge(int age)
{
  //Can't do this
  if(age < 0 || age > 20) return;
  _age = age;
}
```
So we have to `override` the SetAge method in the `Dog` class:
```cs
// In Dog class
public override void SetAge(int age)
{
  if(age < 0 || age > 20) return;
  _age = age;
}
```

#### Why is this useful?
Sometimes we will have a method that will have differences based on which objects inherit it, and it can be modified to fit those differences.

## A fully object-oriented script
Combining everything, we arrive at this script. Feel free to use it for reference.
```cs title="Fully OOP-ified script"
//                                      Abstraction
public abstract class Animal
{
  public string Name;

  //                                    Encapsulation
  private int _age;

  public void SetAge(int age)
  {
    if(age < 0) return;
    _age = age;
  }
  public int GetAge()
  {
    return _age;
  }
}
//                                      Inheritance
class Dog: Animal
{
  public string collarColour;

  //                                    Polymorphism
  public override void SetAge(int age)
  {
    if(age < 0 || age > 20) return;
    _age = age;
  }
}
```