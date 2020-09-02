# Quick Java Reference

## JS ⬄ Java

| Identical in Java and JavaScript   | Java Gotchas for JavaScript Programmers                                                                                                                                                                                                                                                                   |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arithmetical operators             | Java has no separate "exact" comparison operators (`===`, `!==`).<sup>1</sup>                                                                                                                                                                                                                             |
| Ternary statements                 | Double quotes (`"`) must enclose string literals                                                                                                                                                                                                                                                          |
| Basic method invocations           | Single quotes (`'`) enclose character literals. Character literals are numeric values and may not be assigned to type `String` <sup>2</sup>.                                                                                                                                                              |
| Loops (`for`, `while`, `do while`) | Double and single quotes may not be substituted for each other                                                                                                                                                                                                                                            |
| `switch` conditionals              | There are no backtick (\`) string literals. Use [`String.format`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/lang/String.html#format) and [`System.out.printf`](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/io/PrintStream.html#printf) instead.<sup>3</sup> |
| `if`-`then`-`else` conditionals    | There are no top-level functions, only class methods. Top level functions can be emulated to a certain extent with static methods.                                                                                                                                                                        |

<sup>1</sup> Because Java knows the type of all data, there is no reason to
have different comparison operators. All comparisons are by value, this has the
effect that primitive types are always compared like JavaScript `==`, while
reference types (mostly class instances) are always compared like JavaScript
`===`. In JavaScript, there are no primitive data types, which is why JavaScript
requires two different comparison operators.

<sup>2</sup> Character literals can only contain a _single_ character. A single
character string literal (_ie_ `"A"`) is not a character and cannot be assigned
to a `char`. Similarly, a character literal (_ie_ `'A'`) cannot be assigned to a
`String`. A character literal is actually a numeric value that represents the
Unicode value of the quoted character, and may either contain the actual
character, or the character's value in hexadecimal. _IE_ `'A'` = `'\u0041'` = `65`
and `'的'` = '\u7684' = `30340`.

<sup>3</sup> [The full reference to Java string format options](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/Formatter.html#syntax)

## Java primitive data types<sup>1</sup>

| Type                 |          Bits |              Minimum value |             Maximum value | Default value |
| -------------------- | ------------: | -------------------------: | ------------------------: | ------------: |
| **boolean**          | 1<sup>2</sup> |                    `false` |                    `true` |       `false` |
| byte                 |             8 |                       -128 |                       127 |             0 |
| **char**<sup>3</sup> |            16 |            `'\u0000'` or 0 |      `'\uffff'` or 65,535 |    `'\u0000'` |
| short                |            16 |                    -32,768 |                    32,767 |             0 |
| **int**              |            32 |             -2,147,483,648 |             2,147,483,647 |             0 |
| **long**             |            64 | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |            0L |
| float                |            32 |                            |                           |            0f |
| **double**           |            64 |                            |                           |            0d |

<sup>1</sup> Bolded types in the table are the most commonly used types. They
should be used in most cases unless there is a specific reason to use one of the
rarer types. Saving memory is rarely a good reason, as shorter types are often
slower (sometimes significantly so) on modern 64 bit processors.

<sup>2</sup> Insert a little piece on how Java stores boolean values.

<sup>3</sup> `char` is the only unsigned type in Java. This means `char` cannot
hold negative numbers, which is why it can hold twice as high of a positive value
as `short`, despite using the same number of bits.

## Java access modifier visibility

| Modifier      | Declaring class | Declaring package |  Subclasses   |  Everywhere   |
| ------------- | :-------------: | :---------------: | :-----------: | :-----------: |
| public        |   **Visible**   |    **Visible**    |  **Visible**  |  **Visible**  |
| protected     |   **Visible**   |    **Visible**    |  **Visible**  | _Not Visible_ |
| _unspecified_ |   **Visible**   |    **Visible**    | _Not Visible_ | _Not Visible_ |
| private       |   **Visible**   |   _Not Visible_   | _Not Visible_ | _Not Visible_ |

#### Compiling Java for runtime

    javac <package>/*.java
    jar cvfe <name>.jar <package>.<main-class> <package>/*.class
    java -jar <name>.jar
    
#### Casting

```java
int three = (int) 3.14;
```
   
#### Logging 
```java   
System.out.println(...)
```

#### Class Structure 

```java
public class Dog               // accesses modifier - "Class" - name of class
{
    private String breed;      /* a class field(access modifier, data type, name) 
                               fields are pieces of data that classes hold in variables */

    private static int numberofDogs         /* static field (means that its value is 
                                            the same across instances of class fields without 
                                            static can be unique for each instance of a class */

    public Dog(String breed)                /* constructor called with instantiating object instance of class */
    {   
        this.breed = breed;                 /* when an instance of Dog is created the constructor will set this 
                                                field to the data value passed in "this" is used to references 
                                                methods and fields attatched to the class */
    }

    public String getBreed()                /* class method 
                                            (access modifier, data type it returns, name, parameters(empty) */
    {
        return this.breed;
    }

    public void setBreed(String breed)      /* class method 
                                            returns nothing takes one parameter pattern - datatype - param name */
    {
        this.breed = breed;
    }
}
```
        
#### Instantiating a class object

```java
Dog corgi = new Dog("Corgi"); /* instantiates a Dog object which is an instance of class 
                              Dog passes in String breed value into the constructor to set 
                              the field internal to the class */
```
                               
#### Invoking class methods

```java
System.out.println(corgi.getBreed());

corgi.setBreed("Great Dane");
```
    

        
