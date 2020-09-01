# Interfaces and Abstract Classes 


## Abstract Classes [documentation](https://docs.oracle.com/javase/tutorial/java/IandI/abstract.html)

Abstract classes are classes that cannot be instantiated (is not able to create object instances of itself
which can be utilized functionally) but they can be extended to subclasses that can use the fields and 
methods declared in the abstract class. This is useful to extend functionality across a set of sub-classes 
that share commonalities in their structure and function. 

Abstract classes can have both abstract and concrete methods
- Abstract methods need to be overrided in subclass to provide custom functionality
- Concrete methods perform a preset operation outlined in the abstract class

## Declaration 

    public abstract class Person <-- access modifier abstract modifier "class" name
    {
        protected String name;  <-- class fields access modifier type name
        protected int age;
        
        Person() <-- empty constructor can be used if the constructor should set up a part of each sub class
        {         thata remains the same across subclasses
        }
        
        abstract void makeNoise(); <-- abstract method functionality is defined in subclass
        
        public void setName(String name) <-- concrete method functionality is defined here
        {
          this.name = name;
        }
        
        public String getName()
        {
          return this.name;
        }
    }
    
## Extending to Concrete Sub-Classes

  
    public class Adult extends Person <-- declare class extending abstract class
    {
      public Adult(String name, int age) <-- constructor 
      {
        this.name = name; <-- references fields on abstract class
        this.age = age;
      }

      @Override public void makeNoise() <-- override abstract method to perform task specific to subclasses
                                          it is necessary to override every abstract method on the abstract class
      {
        System.out.println("Hi!");
      }

    }
    
Example 2:

    public class Baby extends Person
    {

      public Baby(String name, int age)
      {
        this.name = name;
        this.age = age;
      }

      @Override public void makeNoise()
      {
        Syste.out.println("WAHHH");
      }
    }

## Interfaces [documentation](https://docs.oracle.com/javase/tutorial/java/concepts/interface.html)

interfaces are a structure which is a collection of methods with empty bodies that define a general purpose
but allows one to implement them custom according to the situation in which they are used. Classes can implement 
them to say that their internal methods (which describe actually functionally) conform to the method names
definied in the interface as well as their expected incoming parameters and return value types

#### Declaration

    Interface Person 
    {
        void makeNoise();
        String getName();
        void setName(String name);
    }
    
#### Implement

    public class Adult implements Person <-- declare class implement interface
    {
        private String name; <-- fields are declared in classes unlike with abstract class
        private int age;
        
        public Adult(String name, int age) <-- constructor 
        {
            this.name = name;
            this.age = age;
        }
        
        All methods on interface are implemented
        VVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV
        
         public void setName(String name) 
        {
          this.name = name;
        }
        
        public String getName()
        {
          return this.name;
        }
        
        public void makeNoise()
        {
          System.out.println("Hi");
        }
    }
    
Interfaces can also be to declared to provide some form of general functionality across an application

#### Declaration 2

    interface Filter <- declare filter interface which provides generalized filter methods 
    {
        boolean filterStrings(String s);
        boolean filterInt(int i);
    }
    
    
#### Utilization 

    import java.util.ArrayList;
    import java.util.List;

    public class MainClass <-- set up main class with main method
    {
        public static void main(String[] args)
        {
            List<String> strList = new ArrayList(); <-- declare and set values on a list of strings
            strList.add('a'); 
            strList.add('b'); 
            strList.add('c');

            List<String> aAndB = filterStringList(strList, str -> str == 'a' || str == 'b'); <- filter
            
            // NOTES FOR ABOVE LINE
            
                below a static method has been declared to facilitate filtering a list of strings 
                it is called above and given the string list as the first argument the second arguement
                implements the Filter interface and defines a custom operation that conforms to the expectations
                of the filter methods on the Filter interface (returns a boolean takes in one parameter of a specific
                type)
        }

        public static List<String> filterStringList(List<String> strList, Filter filter)
        
            //NOTES FOR ABOVE LINE 
            
                 function which implements Filter
                 Filter is kind of like a callback 
                 function whose specific operation   
                 are defined in the Lambda Expression above
        {
            List<String> filteredList = new ArrayList<>(); <-- declares empty list to contain filtered elements

            for(String str: strList) <-- iterates through incoming list
            {
                if(filter.filterStrings(str) <-- uses interface method that takes in correct type
                {
                    filteredList.add(str); <-- if elements pass test add to filter list
                }
            }

            return filteredList; <-- return filtered collection of elements 
        }
    }
