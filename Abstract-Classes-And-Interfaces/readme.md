# Interfaces and Abstract Classes

## Abstract Classes [documentation](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)

Abstract classes are classes that cannot be instantiated (is not able
use to create new instance of itself) but which can be subclassed, the
subclasses have access to the fields and methods declared in the
abstract class. This is useful to extend functionality across a set of
sub-classes that share commonalities in their structure and function.

Abstract classes can have both abstract and concrete methods
- Abstract methods need to be overrided in a subclass to provide
  custom functionality. The subclass must implement any abstract
  methods, or be declared abstract itself, otherwise the compiler will
  generate an error.
- Concrete methods perform preset operations outlined in the abstract
  class, but can be overridden.

#### Declaration

```java
public abstract class Person // access modifier abstract modifier class name
{
    protected String name;  // class fields access modifier type name
    protected int age;

    // an empty constructor can be used if subclass are in charge of all
    // field initialization
    Person()
    {
    }

    abstract void makeNoise(); // abstract method functionality is defined
                               // in subclass

    public void setName(String name) // concrete method functionality is
                                     // defined here
    {
      this.name = name;
    }

    public String getName()
    {
      return name;
    }
}
```

#### Extending a concrete subclass from an abstract base

```java
public class Adult extends Person // declare class extending abstract class
{
  public Adult(String name, int age) // constructor
  {
    this.name = name; // references fields af abstract base class
    this.age = age;
  }

 // override abstract method to perform task specific to subclasses it is
 // necessary to override every abstract method on the abstract class if
 // the subclass is not itself abstract
  @Override public void makeNoise()
  {
    System.out.println("Hi!");
  }
}
```

Example 2:

```java
public class Baby extends Person
{

  public Baby(String name, int age)
  {
    this.name = name;
    this.age = age;
  }

  @Override public void makeNoise()
  {
    System.out.println("WAHHH");
  }
}
```

## Interfaces [documentation](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html)

Interfaces are a type which defines a collection of methods with empty bodies
hat define a general purpose but allow one to implement them in a custom manner
according to the requirements of the situation in which they are used. Classes
can implement them to guarantee that their internal methods (which describe
actually functionally) conform to the method names and signatures defined in the
interface. A method's signature is it's name and return type combined with the
names, types, and ordering of it's parameters.

#### Declaration

```java
public interface Person
{
    void makeNoise();
    String getName();
    void setName(String name);
}
```

#### Interface implementation

```java
// declare class and implement interface
public class Adult implements Person
{
    // unlike abstract classes interfaces may not have fields, and
    // implementing classes must declare for themselves any fields they
    // require to aid in the implementation
    private String name;
    private int age;

    public Adult(String name, int age)
    {
        this.name = name;
        this.age = age;
    }

    // unless the implementing class is declared abstract, it must implement
    // all interface methods. Abstract classes implementing an interface
    // should declare any unimplemented interface methods as abstract
    public void setName(String name)
    {
        this.name = name;
    }

    public String getName()
    {
        return name;
    }

    public void makeNoise()
    {
        System.out.println("Hi");
    }
}
```

Interfaces can also be to declared to provide some form of general
functionality across an application

#### Declaration 2

```java
// declare filter interface which provides generalized filter methods
public interface Filter
{
    boolean filterStrings(String s);
    boolean filterInt(int i);
}
```

#### Utilization

```java
import java.util.ArrayList;
import java.util.List;

public class MainClass // set up main class with main method
{
    public static void main(String[] args)
    {
        // declare and set values on a list of strings
        List<String> strList = new ArrayList();
        strList.add('a');
        strList.add('b');
        strList.add('c');

        // Here we call the below defined method filterStringList. It is
        // is called to facilitate filtering a list of strings it is
        // called above and given the string list as the first argument
        // the second arguement implement the Filter interface and define
        // a custom operation that conforms to the expectations of the
        // filter methods on the Filter interface (returns a boolean
        // takes in one parameter of a specific type)
        List<String> aAndB = filterStringList(strList, str -> str == 'a' || str == 'b');
    }

    // Function which implements Filter. Filter utilizes a callback
    // function whose specific operation is defined in the lambda
    // expression in the field aAndB assigned above
    public static List<String> filterStringList(List<String> strList, Filter filter)

    {
        // declares empty list to contain filtered elements
        List<String> filteredList = new ArrayList<>();

        for(String str: strList) // iterates through incoming list
        {
            // uses interface method that takes in correct type
            if(filter.filterStrings(str)
            {
                // if elements pass test add to filter list
                filteredList.add(str);
            }
        }

        return filteredList; // return filtered collection of elements
    }
}
```
