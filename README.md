# Quick Java Reference
## JS => Java

| Java Primitives |     Same as JavaScript                     | Access Modifiers 
| -------------- | -----------------------------------------  | -------------------------------------------------------------------- |
| boolean        |  Arithmatic Operators                      | Public - Open Access                                                 |
| byte (8 bits)  |  Boolean Operators                         | Private - Only accessible within class                               |
| char           |  Function/Method Invocations               | Protected - Accessible within same package/classes in other packages |
| short (32bits) |  Loops (for, while, do while)              | Default(no need to set) - Accessible only within package             |
| int (32 bits)  |  Switch Statements                         | -------------------------------------------------------------------- |
| long (64bits)  |  If-else-if conditionals                   | -------------------------------------------------------------------- |
| float (32 bits)|  Ternary Statement                         | -------------------------------------------------------------------- | 
| double(64bits) | -------------------------------- | -------------------------------------------------------------------- |

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
    

        
