# Data Structures

  -- Additional Documentation
  
   [Collections class](https://docs.oracle.com/javase/7/docs/api/java/util/Collections.html)<space><space>\
   [Iterator interface](https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html)<space><space>\
   [Comparator interface](https://docs.oracle.com/javase/7/docs/api/java/util/Comparator.html)


## Array - [Array Documentation](https://docs.oracle.com/javase/7/docs/api/java/util/Arrays.html)

In Java Arrays are orderable unresizeable collections of data of the same type

#### Declaration
  
    String[] stringArr = [15]; <-- Type (String arr), name, assignment (=), size of array [15];
    
#### Access 

    String str = stringArr[1];
    stringArr[2] = "newString";
 
#### Iterate

    for(String s: stringArr) (for element of type String in the stringArr Array)
    {
       System.out.println;
    }
  
## ArrayList [ArrayList Documentation](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)

In Java ArrayLists are orderable resizable collections of data of the same type


#### Required Imports 
+ java.util.List 
+ java.util.ArrayList

#### Declaration 

```java
List<int> numList = new ArrayList<>(); /* Type (List of type int), name, (=), instantiate ArrayList class object
                                       (shares type implicitly) */
```

#### Access

```java
numList.get(index);
```

####  Append

```java
numList.add(1);  // add to end of list 
numList.add(index, 1); // insert at specific index
```

#### Change

```java
numList.set(index, newValue);
```

#### Iterate 

```java
numList.forEach(ele -> System.out.println(ele)); /* forEach element in numList print ele 
                                                 uses a lambda expression to facilitate iteration */
```

> **SIDE NOTE** - Lambda Expression
>
> The simplest Lambda expression contains a single parameter and an expression\
>     `parameter -> expression`
>
>  To use more then one parameter wrap them in parentheses\
>      `(param1, param2) -> expression`
>
>  expressions must immediatley return a value if you need to perform additional operations
>  in a Lambda expression encapsulate it inside of a code block {}\
>      `parameter -> {...code}`
       
 The first parameter in the ArrayList forEach method takes a Consumer interface class that effectively returns
 each element in the list and allows you to perform operations on each element for each cycle. This interface's
 functionality can be utilized via a Lambda Expression formatted in the same form as the interface (ie. same number
 of parameters, same return type) (more on interfaces later)
 
 
 #### Sort (Low -> High)

```java
import java.util.Collections

    .....

    Collections.sort(numList);
```

## HashMaps - [HashMap Documentation](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)

Hashmaps are collections of pieces of data organized in <key,value> (Entries) pairs this data structure is of flexible size

#### Required Imports
+ java.util.Map;
+ java.util.HashMap;

#### Declare

``java
Map<String, Integer> hashMap = new HashMap<>(): /* Type(Map key of type String value of type Integer)
                                                    name (=) new HashMap class object  */
```                                                     
#### Append

```java
hashMap.put("key" value);
```

#### Search for keys or values

```java
hashMap.containsKey("key");
hashMap.containsValue(value);
```
  
#### Remove <key,value> pair (Entry)

```java
hashMap.remove("key");
```
  
#### Empty HashMap
```java  
hashMap.clear();
```

#### Iterate

```java
for(HashMap.Entry mapElem: hashMap.entrySet()) /* Sets type of iterand to Entry, 
                                                grabs set of entries from hashMap  */
{
  System.out.println(mapElem.getKey()); //reference key for each entry in hashMap
  System.out.println(mapElem.getValue()); //reference value for each entry in hashMap
}
```

#### Sort

HashMaps are unsortable by themselves the entries must be transferred to another data structure in order to be sorted

```java
import java.util.Comparator;
import java.util.ArrayList;
import java.util.List;

....

List<HashMap.Entry> entryList = new ArrayList<>(hashMap.entrySet()); 

entryList.sort(Comparator.comparing(entry -> entry.getKey().toString()));


/* NOTES FOR ABOVE CODE

  Create an ArrayList class object of type HashMap.Entry initilize with the set 
  of entries from your hashMap object

  Call ArrayList's sort method passing in a Comparator interface (facilitates 
  sorting by comparing elements in the list) call the comparing method and in that 
  method use a Lambda expression to set what the sort will compare against 
  whilst sorting in this case the key of each entry cast to a String type   */
```
        
## HashSets - [HashSet documentation](https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html)

Hashsets are a collection of pieces of data stored as values of flexible size where each value is unique 

#### Required Imports
+ Java.util.Set;
+ Java.util.HashSet;

#### Declare

```java
Set<String> stringHashSet = new HashSet<>(); /* (type set with elements type string)
                                                 name = new HashSet class object */
```
#### Append

```java
stringHashSet.add("value");
```

#### Remove

```java
stringHashSet.remove("value");
```

#### Empty HashSet

```java
stringHashSet.clear();
```

#### Iterate 

```java
import java.util.Iterator;

....

Iterator<String> iter = stringHashSet.iterator(); /* declare Iterator of same type as HashSet
                                                  name = iterator returned by HashSet iterator method */

/* Iterator is an interface which takes an iterable data structure and provides methods to move through its elements 
   one at at time */

while(iter.hasNext()) // while there is another element in the data structure
{
  String next = i.next(); /* grabs next value in data structure starts at first value 
                              moves the iterator to the next element in the data structure 
                              in each loop (moves while loop to end condition) */
  System.out.println(next);
}
```   
    
## Sort 

HashSets are not sortable on their own and must be converted to another data structure in order to be sorted 

```java
import java.util.List;
import java.util.ArrayList;
import java.util.Collections;

...

List<String> setList = new ArrayList<>(stringHashSet); /* List of same type as HashSet
                                                       name = new ArrayList class object 
                                                       initilized with values in HashSet */

Collections.sort(setList); /* utilizes the Collections class's sort method to sort the list
                               in ascending order */
```
        




    
   
