# Quick Java Reference

## JS <=> Java

| Same as JavaScript                 | Java Gotchas for JavaScript Programmers                                                                                           |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Arithmetical operators             | Java has no separate "exact" comparison operators (`===`, `!==`)                                                                  |
| Ternary statements                 | Double quotes (`"`) must enclose string literals                                                                                  |
| Basic method invocations           | Single quotes (`'`) enclose character literals and must be assigned to type `char`.                                               |
| Loops (`for`, `while`, `do while`) | Double and single quotes may not be substituted for each other                                                                    |
| `switch` conditionals              | There are no backtick (\`) string literals. Use `String.format` and `System.out.printf` instead.                                  |
| `if`-`then`-`else` conditionals    | There are no top-level functions, only class methods. Top level functions can be emulated to a certain extent with static methods |

## Java primitive data types

| Type        | Bits |              Minimum value |             Maximum value | Default value |
| ----------- | ---: | -------------------------: | ------------------------: | ------------: |
| **boolean** |      |                    `false` |                    `true` |       `false` |
| byte        |    8 |                       -128 |                       127 |             0 |
| **char**    |   16 |                   '\u0000' |                  '\uffff' |      '\u0000' |
| short       |   16 |                    -32,768 |                    32,767 |             0 |
| **int**     |   32 |             -2,147,483,648 |             2,147,483,647 |             0 |
| **long**    |   64 | -9,223,372,036,854,775,808 | 9,223,372,036,854,775,807 |            0L |
| float       |   32 |                            |                           |            0f |
| **double**  |   64 |                            |                           |            0d |

- Bolded types in the above table are the most commonly used

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
    
    int three = (int) 3.14;
   
#### Logging 
    
    System.out.println(...)

#### Class Structure 

    public class Dog               <--- accesses modifier - "Class" - name of class
    {
        private String breed;      <--- a class field(access modifier, data type, name) 
                                   fields are pieces of data that classes hold in variables
                              
        private static int numberofDogs         <---- static field (means that its value is 
                                                the same across instances of class fields without 
                                                static can be unique for each instance of a class
                                        
        public Dog(String breed)                <--- constructor called with instantiating object instance of class
        {   
            this.breed = breed;                 <-- when an instance of Dog is created the constructor will set this 
                                                    field to the data value passed in "this" is used to references 
                                                    methods and fields attatched to the class
        }
        
        public String getBreed()                <-- class method 
                                                (access modifier, data type it returns, name, parameters(empty)
        {
            return this.breed;
        }

        public void setBreed(String breed)      <-- class method 
                                                returns nothing takes one parameter pattern - datatype - param name
        {
            this.breed = breed;
        }
    }
        
#### Instantiating a class object

    Dog corgi = new Dog("Corgi"); <-- instantiates a Dog object which is an instance of class 
                                  Dog passes in String breed value into the constructor to set 
                                  the field internal to the class
                               
#### Invoking class methods
    
    System.out.println(corgi.getBreed());
    
    corgi.setBreed("Great Dane");
    

        
