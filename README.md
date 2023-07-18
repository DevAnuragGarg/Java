# Java
Some useful info about

A class is a blueprint for an object. It tells virtual machine how to make an object of that particular type.

=======
Variables comes in two flavors: primitive and reference. Variable must always be declared with a name and a type. A primitive variable is the bits representing the value. A reference variable is the bits representing a way to get an object on the heap

=======
Arrays are always objects, whether they are declared to hold the primitives or object references. They are stored in heap

=======
Difference between package private, public, protected, and private
- A private member variable is accessible within the same class.
- A package private variable (member variable with no access specifier) is accessible within all classes in the same package.
- A protected variable is accessible within all classes in the same package and within subclasses in other packages.
- A public member is accessible to all classes.

=======
Encapsulation: Hiding the instance variables from outside world. Using setter method, we can validate or put on check if it is double. May be method will reject it or throw an exception. It is a principle of wrapping data (variables) and code together as a single unit. It is one of the four OOP concepts. Data can only be accessed by public methods thus making the private fields and their implementation hidden for outside classes. That’s why encapsulation is known as data hiding.

=======
Advantages of encapsulation
- It improves maintainability and flexibility and re-usability. Hence the code can be maintained at any point of time without breaking the classes that uses the code. This improves the re-usability of the underlying class.
- The fields can be made read-only (If we don’t define setter methods in the class) or write-only (If we don’t define the getter methods in the class). For e.g. If we have a field(or variable) that we don’t want to be changed so we simply define the variable as private and instead of set and get both we just need to define the get method for that variable. Since the set method is not present there is no way an outside class can modify the value of that field.
- User would not be knowing what is going on behind the scene. They would only be knowing that to update a field call set method and to read a field call get method but what these set and get methods are doing is purely hidden from them.
- With Java Encapsulation, you can hide (restrict access) to critical data members in your code, which improves security

=======
Abstraction: Abstraction is a process of hiding the implementation details from the user. Only the functionality will be provided to the user. In Java, abstraction is achieved using abstract classes and interfaces. Abstraction unifies multiple and different objects into one concept, describing the common properties of those objects. Vehicle is an abstraction of CAR, TRUCK, MOTORCYCLE.
public abstract class Employee {
	private String name;
	private int paymentPerHour;
	public Employee(String name, int paymentPerHour) {
		this.name = name;
		this.paymentPerHour = paymentPerHour;
	}
	public abstract int calculateSalary();
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getPaymentPerHour() {
		return paymentPerHour;
	}
	public void setPaymentPerHour(int paymentPerHour) {
		this.paymentPerHour = paymentPerHour;
	}
}
public class Contractor extends Employee {	
	private int workingHours;
	public Contractor(String name, int paymentPerHour, int workingHours) {
		super(name, paymentPerHour);
		this.workingHours = workingHours;
	}
	@Override
	public int calculateSalary() {
		return getPaymentPerHour() * workingHours;
	}
}
public class FullTimeEmployee extends Employee {
	public FullTimeEmployee(String name, int paymentPerHour) {
		super(name, paymentPerHour);
	}
	@Override
	public int calculateSalary() {
		return getPaymentPerHour() * 8;
	}
}
=======
Inheritance: An inheritance relationship means that the subclass inherits the members of the superclass. Public methods are inherited, private methods are not. Benefit of Inheritance is code re-usability and if you need to modify, you have to modify at one place only. You also get to use the polymorphism. Instance variables are not overridden. Java doesn't support multiple inheritance. It is a property of an object to aquire all the properties and behaviour of its parent object. It has IS-A relationship between child parent classes.

=======
Polymorphism: Polymorphism is the ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object. Any Java object that can pass more than one IS-A test is considered to be polymorphic. In Java, all Java objects are polymorphic since any object will pass the IS-A test for their own type and for the class Object. Compiler just checks if the method is present in the superclass or subclass. Just see the any of the method is reachable. But it is JVM which takes care which method to call. In inheritance IS-A relationship works in only 1 direction. A superclass won't necessarily know about its subclass. There is no sort of reverse or backwards inheritance. In other words, polymorphism allows you define one interface and have multiple implementations.

=======
Object class: The Object class, in the java.lang package, sits at the top of the class hierarchy tree. Every class is a descendant, direct or indirect, of the Object class. Every class you use or write inherits the instance methods of Object. You need not use any of these methods, but, if you choose to do so, you may need to override them with code that is specific to your class. The methods inherited from Object that are discussed in this section are:
- protected Object clone() throws CloneNotSupportedException
      Creates and returns a copy of this object.
- public boolean equals(Object obj)
      Indicates whether some other object is "equal to" this one.
- protected void finalize() throws Throwable
      Called by the garbage collector on an object when garbage
      collection determines that there are no more references to the object
- public final Class getClass()
      Returns the runtime class of an object.
- public int hashCode()
      Returns a hash code value for the object.
- public String toString()
      Returns a string representation of the object.

The notify, notifyAll, and wait methods of Object all play a part in synchronizing the activities of independently running threads in a program
- public final void notify()
- public final void notifyAll()
- public final void wait()
- public final void wait(long timeout)
- public final void wait(long timeout, int nanosecond)

=======
Every class has some set of functions: equals, hashCode, toString, getClass. You can override only some of them, not every method. getClass method is final, it can't be overridden. No, Object class is not abstract. It has some by-default implementation. 

=======
Can you inherit a private class?? There is no such thing as private class. private classes are the inner classes. Java allows only public and default modifier for top level classes in java.

=======
Can we declare a class static: Yes and No. You cannot make a top level class static in Java, the compiler will not allow it, but you can make a nested class static in Java. A top level class is a class which is not inside another class.

=======
In what cases class can't be sub-classed:
1) A non public class can be sub-classed only by the classes in the same package as class. Classes in other packages can't subclass the non-public class. 
2) A class can be stopped being sub-classed by the class modifier final. A final means that it's the end of the inheritance line. Nobody can extend the final class. 
3) If the class has only the private constructors it can't be sub-classed.

=======
Why would you like to make the class final?? If you need security, the security of knowing that the methods will always work the way you have wrote them. The String class for example, is final. If you want to make a method from being overridden, mark it with the final modifier.

=======
Abstract Class: The classes which can't be instantiated. Interface: 100% abstract classes 
Ex. Animal animal = new Hippo(); {Hippo extents Animal}
Animal animal = new Dog(); {Dog extents Animal}
Animal animal = new Animal(); Creating an animal object is of no use. But we need the Animal class for the polymorphism and Inheritance. Actually we don't want Animal class to get instantiated. So no one will try to use new parameter for Animal class. We declare the Animal class as abstract. On the other hand the classes which can be instantiated are called concrete classes. Compiler won't let you instantiate an abstract class. An abstract class has no use, no value, no purpose until extended. Declaring the method abstract means the method has to be overridden. If class is declared as abstract, compiler will stop any code, anywhere, from ever creating an instance of that type. You can still use that abstract type as a reference type. An abstract class means the class must be extended, an abstract method means the method must be overridden. If you declare the method abstract, you have describe the class abstract too. You must implement all the abstract methods. Implementing the abstract method is same as overriding the method. Abstract methods don't have a body, they exist solely for polymorphism. 

========
Import does not make the class bigger. It is not same as include in C. An import is simply the way you give Java the full name of a class. Classes like String or System you no need to import as these classes are considered as so fundamental, that no need to specifically import the full name. 

========
Why you are not allowed to extend two classes: Java doesn’t allow multiple inheritance. Deadly diamond of death.:-> A and B class inherits C. D inherits A and B. If both the A and B has implemented the method from C, then if we call that method from D object which one would be called.

========
Constructor has the code that runs when you instantiate an object. In other words, the code that runs when you say new on a class type. Constructors are not inherited. Private constructors means no one from outside the class can instantiate the class. Even abstract class has the constructors. All the super constructors are run when subclass is initiated. For an object to be fully formed, all the superclass parts of itself must be fully formed and that's why super constructors must run. When a constructor is run, it will run all the way to Object class. First super constructor is completed then subclass constructor is completed. The compiler will put a call to super() in each of your overloaded constructor. The compiler inserted call to super() is always  a no-arg call. If the superclass has overloaded constructors, only the no-arg one is called. The super class parts of an object has to be fully formed before the subclass parts can be constructed. Use this() to call a constructor from overloaded constructor in same class. this() can only be used only in constructor and should be the first line of any constructor. A constructor can have a call to super() or this() but not both. Even super should be the first statement of the constructor.

========
Why abstract has constructors: A constructor in Java doesn't actually "build" the object, it is used to initialize fields. Imagine that your abstract class has fields x and y, and that you always want them to be initialized in a certain way, no matter what actual concrete subclass is eventually created. So you create a constructor and initialize these fields. Now, if you have two different subclasses of your abstract class, when you instantiate them their constructors will be called, and then the parent constructor will be called and the fields will be initialized. If you don't do anything, the default constructor of the parent will be called. However, you can use the super keyword to invoke specific constructor on the parent class.

========
Static: This will let a method run without any instance of the class. You can't use an instance variable from inside a static method. Compile thinks I don't know which object's instance variable you are talking about. Static variables are shared. All instances of the same class share a single copy of the static variables. Static variables are initialized when the class is loaded. Static variables are initialized before any object of that class can be created. Static variables in a class are initialized before any static method of the class runs. 

========
Static final variables are constants. A variable marked final means once initialized it can never change. In other words, the value of the static final variable will stay the same as long as the class is loaded. Constant variable names should be in all caps. If you are going to use a static member a few times, we think you should avoid static imports, to help keep the code more readable. It is stored in the heap referenced by the class definition. If you think about it, it has nothing to do with stack because there is no scope.

========
ArrayList<int> is not possible. Compile time error. Primitives are not allowed. You can specify only classes or interfaces.

========
Auto-boxing: Putting int into Integer automatically.

========
Exception: One method will catch the exception what another method throws. An exception is always thrown back to the caller. The compiler checks for everything except Runtime exception. Exceptions that are not subclass of runtime exception are checked for by the compiler. They are called checked exceptions. If you throw an exception in your code you must declare it using the throws keyword in your method declaration. You can throw, catch and declare Runtime exceptions, but you don't have to, and compile won't check. A try/catch is for handling exceptional situations, not flaws in your code. Use your catch blocks to try to recover from situations you can't guarantee will succeed.

=======
All the exception types are subclasses of the built in class Throwable. Error class is related to java run time error that can’t be caught usually, RuntimeExecption is subclass of Exception class which contains all the exceptions that can be caught.

=======
Difference between throws and throw
throw: throw new Exception("You have some exception"), throw new IOException("Connection failed!!")
throws: public int myMethod() throws IOException, ArithmeticException, NullPointerException {}

=======
A finally block is where you put the code that must run regardless of an exception. Method can throw more then one exception. Exceptions are polymorphic. The benefit of exception is that a method doesn't have to explicitly declare every possible exception it might throw, it can declare superclass of the exceptions. Try to write catch block for exception that you need to handle uniquely. If you don't want to handle an exception, you can duck it by declaring it. You can't have a catch or finally without a try. A try must be followed either a catch or a finally. You can't put code between the try and catch. A try with only a finally must still declare the exception. 

=======
If only try-finally is present: If any of the code in the try block can throw a checked exception, it has to appear in the throws clause of the method signature. If an unchecked exception is thrown, it's bubbled out of the method.

=======
public class Catch {
    public static void main(String[] args) {
        try {
            throw new java.io.IOException();
        } catch (java.io.IOException exception) {
            System.err.println("In catch IOException: "+ exception.getClass());
            throw new RuntimeException();
        } catch (Exception exception) {
            System.err.println("In catch Exception: "+ exception.getClass());
        } finally {
            System.err.println("In finally");
        }
    }
}
In catch IOException: class java.io.IOException
In finally
Exception in thread "main" java.lang.RuntimeException at Catch.main(Catch.java:8)

=======
try{
    return 1;
}finally {
    System.out.println("Finally");
    return 2;
}
Answer: Finally, 2

=======
try {
    abc = 18/0;
}catch (ArithmeticException e){
    return;
}finally {
   System.out.println("ABC");
}
System.out.println("DEF");
Answer: ABC

=======
The only times finally won't be called are:
1) If you invoke System.exit();
2) If the JVM crashes first;
3) If the JVM reaches an infinite loop (or some other non-interruptible, non-terminating statement) in the try or catch block;
4) If the OS forcibly terminates the JVM process; e.g. "kill -9 " on UNIX.
5) If the host system dies; e.g. power failure, hardware error, OS panic, etcetera.

=======
class Main { 
   public static void main(String args[]) { 
      try { 
         throw 10; 
      } 
      catch(int e) { 
         System.out.println("Got the  Exception " + e); 
      } 
  } 
} 
In Java only Throwable objects (Throwable objects are instances of any subclass of the Throwable class) can be thrown as exception. So basic data type can no be thrown at all. Compile time error.

=======
Serialization is a mechanism of converting the state of an object into a byte stream. Deserialization is the reverse process where the byte stream is used to recreate the actual Java object in memory.

=======
Serialized objects save the values of the instance variables, so that identical instance can be brought back to life on the heap. When an object is serialized, all the objects it refers to from instance variables are also serialized. And all the objects those objects refer to are serialized. Serialization saves the entire object graph. All objects referenced by instance variables, starting with the object being serialized. If any superclass of a class is serializable, the subclass is automatically serializable even if the subclass doesn't explicitly declare implements Serializable. Either the entire object graph is serialized completely or serialization fails. Mark an instance variable as transient if you don't want to save the state of that variable. Sometimes your variable is dependent upon run-time calculations, so you don't want to serialize that variable, just mark that variable as transient. Even for the security purpose you sometimes don't want the class to be serializable. If the class itself is extend-able (not final) you can make a serializable subclass, and just substitute the subclass everywhere your code is expecting the superclass type. If we de-serialize the subclass of a non-serializable superclass, the superclass constructor will run just as though a new object of that type were being created. If your data will be used by only the JAVA program then use Serialization and if your data is used by other programs then write a plain text file.

=======
When an object is de-serialized, the JVM attempts to bring back to life by making a new object on the heap that has the same state the serialized object had at the time it was serialized except the transient variables, which come back either null(for object reference) or as default primitive values. The object is read from the stream. The JVM determines the object's class type. The JVM attempts to find and load the object's class. If the JVM can't load the class, the JVM throws an exception and the deserialization fails. A new object is given space on the heap, but the serialized object's constructor does not RUN. If constructor ran, it would restore the state of the object back to it's original new state. If the object has a non-serializable class somewhere up its inheritance tree, the constructor for that non-serializable class will run along with any constructors above that. Once constructor begins, you can't stop, means all super classes, beginning with the first non-serializable one, will re-initialize their state. Serialization is also used to send the objects over a network connection. Static variables are not serialized. As static means only once per class. When an object is de-serialized, it will have whatever static variables its class currently has. So, don't make serializable objects dependent on a dynamically- changing static variable. You can save an object's state by serializing the object.

=======
Advantages of Serialization
1. To save/persist state of an object.
2. To travel an object across a network.

=======
SerialVersionUID: The Serialization runtime associates a version number with each Serializable class called a SerialVersionUID, which is used during Deserialization to verify that sender and receiver of a serialized object have loaded classes for that object which are compatible with respect to serialization. If the receiver has loaded a class for the object that has different UID than that of corresponding sender’s class, the Deserialization will result in an InvalidClassException. A Serializable class can declare its own UID explicitly by declaring a field name. It must be static, final and of type long. Each time an object is serialized, the object is stamped with a version ID number for object's class. The ID is called the serialVersion UID. As an object is being de-serialized, if the class has changed since the object was serialized, the class could have a different serialVersionID, and deserialization will fail. But we can control this. If you think there is any possibility that your class might evolve, put a serial version ID in your class. But the responsibility will always be yours.

=======
public class Student implements Serializable{  
	int id;  
	String name;  
	public Student(int id, String name) {  
		this.id = id;  
		this.name = name;  
 	}  
}  

=======
A file object represents the name and path of a file or directory on disk but it does not represent or give you access to, the data in the file. Buffers give you a temporary holding place to group things until the holder is full. BufferedWriter writer = new BufferedWriter(new FileWriter(aFile)); By chaining buffered writer into file writer, buffered writer will hold all the stuff you write to it until it's full. Only when the buffer is full will the file writer actually be told to write to file on disk. If you want to send the data before the buffer is full, you can flush it writer.flush().

=======
Reading from file
FileReader fileReader = new FileReader(new File("abc.txt"));
BufferedReader reader = new BufferedReader(fileReader);
String line = null;
while((line = reader.readLine()) != null){
	System.out.println(line);
}
reader.close();

=======
Client connects to server by establishing a Socket connection. Client sends a message to the server. Client gets a message from the server. For making a socket connection you want to know 2 things: Who is it and which port it is running on?. In other words, IP address and TCP port number. A socket is an object that represents a network connection between two machines. A socket connection mean the two machines have information about each other, including IP and TCP port. A TCP is just a number, a 16 bit number that identifies a specific program on the server. Your INTERNET web server runs on port 80. That is a standard. FTP: 20, POP3 mail server: 110, Telnet server: 23, SMTP: 25. These numbers represents the logical connection to a particular piece of software running on server. Without port numbers, the server would have no way of knowing which application a client wanted to connect to. The TCP port numbers from 0 to 1023 are reserved for well known services. We don't use them for our programs. 

=======
Two applications on the same server on the same port, it is not possible. If you try to bind a program to a port that is already in use, you'll get a BindException. To bind a program to a port just means starting up a server application and telling it to run on a particular port. To communicate over a Socket connection use streams. To read the message, use BufferedReader.

=======
A socket is one endpoint of a two-way communication link between two programs running on the network. A socket is bound to a port number so that the TCP layer can identify the application that data is destined to be sent to. An endpoint is a combination of an IP address and a port number. 
Socket socket = new Socket("102.0.0.1", 5000);
Make an input stream reader chained to Socket low-level input stream. Input stream reader is a bridge between a low level byte stream and a high level character stream. InputStreamReader stream = new InputStreamReader(socket.getInputStream());
Chain the buffered reader to the InputStramReader which was chained to the low level connection stream we got from the socket.
BufferedReader reader = new BufferedReader(stream); reader.readLine();
To write data to a socket use print writer.
PrintWriter writer = new PrintWriter(socket.getOutputStream());
Chaining a print writer to the socket's output stream we can write strings to socket connection.
writer.print("message");

=======
When do you get messages from the server??
Method 1: Polling , Poll the server every 20 seconds. You start hitting the server needlessly. Insufficient.
Method 2: Read something, when user sends a message. Stupid method. 
Method 3: Read messages as soon as they're sent from the server. Most efficient. A loop somewhere that always waiting to read from server. Here comes the concept of threads.

=======
Inside Collection Framework, there exist two Interface Collection interface(90% of collection framework) and rest map interface. People usually call COLLECTION AND COLLECTION FRAMEWORK one and the same but in reality Collection framework comprises of map and collection interface. Collection is an interface, rather than root interface in collection hierarchy. It comprises of main Set, List, Queue, Deque interfaces from which classes like classes ArrayList, Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet are created. Collections is an utility class present in java.util. package to define several static utility method (like sorting, searching) for collection object.

             Collection                Map
         /     /    \      \            |
        /      /      \     \           |
     Set    List    Queue  Dequeue   SortedMap
     /
    /
 SortedSet 
Two things to keep in mind: Sorting and Ordering 

=======
Set: A Set is a Collection that cannot contain duplicate elements. Set also adds a stronger contract on the behavior of the equals and hashCode operations, allowing Set instances to be compared meaningfully

HashSet: It implements the Set interface. HashSets are used to store a collection of unique elements. HashSet allows null value. HashSet is an unordered collection. It does not maintain the order in which the elements are inserted. HashSet is not thread-safe. HashSet internally uses a HashMap to store its elements. Duplicate values are not allowed. HashSet implementation is not synchronized.

TreeSet: Java TreeSet class implements the SortedSet interface that uses a tree for storage. The objects of the TreeSet class are stored in ascending order which is done using the comparator. Java TreeSet class contains unique elements only like HashSet. Java TreeSet class doesn't allow null element. Java TreeSet class is non synchronized. Java TreeSet class access and retrieval times are quiet fast. It is created using tree: Red-Black tree.

=======
Difference between HashSet and TreeSet:
1) First major difference between HashSet and TreeSet is performance. HashSet is faster than TreeSet and should be preferred choice if sorting of element is not required.
2) Second difference between HashSet and TreeSet is that HashSet allows null object but TreeSet doesn't allow null Object and throw NullPointerException, Why, because TreeSet uses compareTo() method to compare keys and compareTo() will throw java.lang.NullPointerException.
3) Another significant difference between HashSet and TreeSet is that , HashSet is backed by HashMap while TreeSet is backed by TreeMap in Java.
4) One more difference between HashSet and TreeSet which is worth remembering is that HashSet uses equals() method to compare two object in Set and for detecting duplicates while TreeSet uses compareTo() method for same purpose. if equals() and compareTo() are not consistent, i.e. for two equal object equals should return true while compareTo() should return zero, than it will break contract of Set interface and will allow duplicates in Set implementations like TreeSet
5) Now most important difference between HashSet and TreeSet is ordering. HashSet doesn't guaranteed any order while TreeSet maintains objects in Sorted order defined by either Comparable or Comparator method in Java.

=======
Implementation of HashSet: 
public class HashSet extends AbstractSet implements Set, Cloneable, java.io.Serializable{
    private transient HashMap<E,Object> map;
    // Dummy value to associate with an Object in the backing Map
    private static final Object PRESENT = new Object();
    public HashSet() {
        map = new HashMap<>();
    }
    public boolean add(E e) {
        return map.put(e, PRESENT)==null;
    }
    ....
}
Here a dummy object is created. Which is used to store the value. The same value is stored in the HashMap using dummy object. The equals method plays an important role.

=======
Implementation of TreeSet:
public class TreeSet<E> extends AbstractSet<E> implements NavigableSet<E>, Cloneable, java.io.Serializable{
    private transient NavigableMap<E,Object> map;
    // Dummy value to associate with an Object in the backing Map
    private static final Object PRESENT = new Object();
    public TreeSet() {
        this(new TreeMap<E,Object>());
    }
    // SOME CODE ,i.e Other methods in TreeSet
    public boolean add(E e) {
        return map.put(e, PRESENT)==null;
    }   
    // SOME CODE ,i.e Other methods in TreeSet
}
Internally it used TreeMap which internally uses HashMap only. Here comparator/comparable is used. Dummy  value that is ( new Object () ) which is referred by Object reference PRESENT .

=======
List: The Java List interface, java.util.List, represents an ordered sequence of objects. The elements contained in a Java List can be inserted, accessed, iterated and removed according to the order in which they appear internally in the Java List. Against set list maintains order and can have same object listed again.

ArrayList: It internally uses an array to store the elements. Just like arrays, It allows you to retrieve the elements by their index. It allows duplicate and null values. It is an ordered collection. It maintains the insertion order of the elements. It is a re-sizable array, also called a dynamic array. Compared to linked list it is better for storing and accessing data.

LinkedList: It uses a doubly linked list to store the elements. It can contain duplicate elements. It maintains insertion order. It is non synchronized. It can be used as a list, stack or queue. Manipulation with LinkedList is faster than ArrayList because it uses a doubly linked list. 

Vector: It implements a dynamic array. It is similar to ArrayList, but with two differences: It is synchronized.
It contains many legacy methods that are not part of the collections framework.

Stack: It actually implements the Java List interface, but you rarely use a Stack as a List. You can push elements to the top of a Java Stack and pop them again, meaning read and remove the elements from the top of the stack.

=======
Queue: Java Queue interface orders the element in FIFO(First In First Out) manner. In FIFO, first element is removed first and last element is removed at last.

Deque: The java.util.Deque interface is a subtype of the java.util.Queue interface. It is related to the double-ended queue that supports addition or removal of elements from either end of the data structure, it can be used as a queue (first-in-first-out/FIFO) or as a stack (last-in-first-out/LIFO). These are faster than Stack and LinkedList.

LinkedList: is a pretty standard dequeue implementation. Means doubly linked list.

PriorityQueue class provides the facility of using queue. But it does not orders the elements in FIFO manner. It inherits AbstractQueue class. It stores its elements internally according to their natural order (if they implement Comparable), or according to a Comparator passed to the PriorityQueue.

ArrayDeque: It apply re sizable-array in addition to the implementation of the Deque interface. It is also known as Array Double Ended Queue or Array Deck. This is a special kind of array that grows and allows users to add or remove an element from both the sides of the queue. They are not thread-safe. Null elements are prohibited in the ArrayDeque. ArrayDeque class is likely to be faster than Stack when used as a stack. ArrayDeque class is likely to be faster than LinkedList when used as a queue.

=======
Map: It contains values on the basis of key, i.e. key and value pair. Each key and value pair is known as an entry. A Map contains unique keys. A Map is useful if you have to search, update or delete elements on the basis of a key. There are two interfaces for implementing Map in java: Map and SortedMap, and three classes: HashMap, LinkedHashMap, and TreeMap.

SortedMap: interface extends Map. It ensures that the entries are maintained in an ascending key order. If we don’t provide any Comparator (which should be able to accept key of the map) while creating SortedMap, all key elements of map must have implemented Comparable interface to ensure ordering. It does not allow any null key or null value.

TreeMap: TreeMap is Red-Black tree based NavigableMap implementation. It is sorted according to the natural ordering of its keys. It is unsynchronized collection class. Java TreeMap contains only unique elements. You may also provide a custom Comparator to the TreeMap at the time of creation to let it sort the keys using the supplied Comparator

HashMap: HashMap is a Map based collection class that is used for storing Key & value pairs, it is denoted as HashMap<Key, Value> or HashMap<K, V>. This class makes no guarantees as to the order of the map. It is similar to the HashTable class except that it is unsynchronized and permits null values and one null key. It is not an ordered collection which means it does not return the keys and values in the same order in which they have been inserted into the HashMap. It does not sort the stored keys and Values.

LinkedHashMap: It is the implementation of Map, it inherits HashMap class. It allows null values and null key. It maintains insertion order. So consider using a LinkedHashMap when you want a Map with its key-value pairs are sorted by their insertion order. This implementation differs from HashMap in that it maintains a doubly-linked list running through all of its entries. This linked list defines the iteration ordering, which is normally the order in which keys were inserted into the map (insertion-order). 

=======
sort() method can only take lists of comparable objects. An object which is not a subtype of Comparable, you cannot sort that object. String class doesn't extend comparable but implements it. So for the Objects to work on sort(), the POJO class of Object has to implement Comparable which in turn implement compateTo() method. It compares the values between one variable of two objects. So, issue arises: if we want to sort using two variables one is name and other is city. For that comparator comes into picture.

=======
Comparator is external to element type, its a separate class. sort() method use the Comparator instead of element's own compateTo() method. If you pass a comparator to sort() method. If you pass a comparator to sort() method, the sort order is determined by Comparator rather than the element's own compareTo() method.

=======
Reference equality: when there are two references and one object on heap. If you call hashCode for both references you will get same value. If you want to know if two references are really referring to same object, use the == operator, which compares the bits in the variables.
Object equality: Two references, two objects on heap, but the objects are considered meaningfully equivalent. If you want to treat two different objects as same, you must override hashCode and equal method.

=======
If two objects have same hashcode, it is not meant that they are equal, but if they are equal their hashcode must be same. If you don't override hashcode() in a class, no two objects of that type can be ever considered equal. The default behavior of equal is ==. If you don't override equals, no two objects can be equal since references to two objects will always have a different bit pattern. Hash code is faster to access.

=======
Overriding just means that a subclass re-defines one of its inherited methods when it needs to change or extend the behavior of that method. Arguments and return types(may be compatible) of your overriding methods must look to the outside world exactly like the overridden method in the superclass. Method can't be less accessible. Access level must be same or more friendlier.

=======
You can't override a private method, because outside of Super, you can't even call the method. Even in subclasses. You can define another method with the same name, but then the superclass still has its method, and the subclass has its own separate method.

=======
Overloading: No polymorphism is involved with overloaded methods. Overloading lets you make multiple versions of a methods. Overloading method creates a new method with same name. It has nothing to do with the inheritance and polymorphism. You are free to change the return types in overloaded methods, as long as argument lists are different. You can't change only the return type. Method overloading is nothing more than having two methods with same name but different argument lists. You can vary the access levels in any direction.

=======
Overloading happens at compile-time while Overriding happens at runtime: The binding of overloaded method call to its definition happens at compile-time however binding of overridden method call to its definition happens at runtime.

=======
Static methods can be overloaded which means a class can have more than one static method of same name. Static methods cannot be overridden, even if you declare a same static method in child class it has nothing to do with the same method of parent class as overridden static methods are chosen by the reference class and not by the class of the object. The most basic difference is that overloading is being done in the same class while for overriding base and child classes are required.

=======
Static binding is being used for overloaded methods and dynamic binding is being used for overridden/overriding methods. Performance: Overloading gives better performance compared to overriding. The reason is that the binding of overridden methods is being done at runtime.

=======
Argument list should be different while doing method overloading. Argument list should be same in method Overriding. It is also a good practice to annotate overridden methods with @Override to make the compiler be able to notify you if child is, indeed, overriding parent's class method during compile-time.

=======
Can an Interface implement another Interface: Yes, an interface can implement another interface (and more than one), but it needs to use extends, rather than implements keyword. And while you can not remove methods from parent interface, you can add new ones freely to your new interface.

=======
It should be noted that standard class hierarchy does not apply to generic types. It means that Integer in List<Integer> is not inherited from <Number> - it is actually inherited directly from <Object>. You can still put some constraints on what classes can be passed as a parameter into a generic by using wildcards like <?>, <? extends MyCustomClass> or <? super Number>.

=======
Composition vs Inheritance: Composition is the design technique in object-oriented programming to implement has-a relationship between objects. Composition in java is achieved by using instance variables of other objects. For example, Person has-a Job relationship is implemented like below in java object-oriented programming.
public class Job {
	// variables, methods etc.
}
public class Person {
    //composition has-a relationship
    private Job job;
}
Inheritance is the design technique in object oriented programming to implement is-a relationship between objects. Both composition and inheritance promotes code reuse through different approaches. So which one to choose? How to compare composition vs inheritance. You must have heard that in programming you should favor composition over inheritance. Let's see some of the reasons that will help you in choosing composition vs inheritance. Inheritance is tightly coupled whereas composition is loosely coupled. Let's assume we have below classes with inheritance.
public class ClassA {
	public void foo(){	
	}
}
class ClassB extends ClassA{
	public void bar(){		
	}
}
For simplicity we have both the superclass and subclass in single package. But mostly they will be in separate code-base. There could be many classes extending the superclass ClassA. A very common example of this situation is extending Exception class. Now let's say ClassA implementation is changed like below, a new method bar() is added.
public class ClassA {
	public void foo(){	
	}
	public int bar(){
		return 0;
	}
}
As soon as you start using new ClassA implementation, you will get compile time error in ClassB as The return type is incompatible with ClassA.bar(). The solution would be to change either the superclass or the subclass bar() method to make them compatible. If you would have used Composition over inheritance, you will never face this problem. A simple example of ClassB implementation using Composition can be like below.
class ClassB{
	ClassA classA = new ClassA();
	public void bar(){
		classA.foo();
		classA.bar();
	}
}
There is no access control in inheritance whereas access can be restricted in composition. We expose all the superclass methods to the other classes having access to subclass. So if a new method is introduced or there are security holes in the superclass, subclass becomes vulnerable. Since in composition we choose which methods to use, it's more secure than inheritance. For example, we can provide ClassA foo() method exposure to other classes using below code in ClassB.
class ClassB {
	ClassA classA = new ClassA();
	public void foo(){
		classA.foo();
	}	
	public void bar(){	
	}
}
This is one of the major advantage of composition over inheritance.

=======
Difference between static and dynamic binding: Static binding in Java occurs during compile time while dynamic binding occurs during runtime. private, final and static methods and variables use static binding and are bonded by compiler while virtual methods are bonded during runtime based upon runtime object. Static binding uses Type (class in Java) information for binding while dynamic binding uses object to resolve binding. Overloaded methods are bonded using static binding while overridden methods are bonded using dynamic binding at runtime.

=======
Can you overload main method: Yes, you can overload main method but only method with signature public static void main(String[] args) will be used when your class is invoked by JVM.

=======
Can we change only return type while method overloading: You can not. If we change only return type, it will become ambiguous for compiler to figure out which method to call.That is why you can not change only return type.

=======
For overriding, arguments must not change. Final method	Can not be overridden. Static method cannot be overridden. Constructor cannot be overridden. Access Modifier must not be more restrictive. Can be less restrictive. Return type can’t change except for covariant (subtype) returns. 

=======
Method hiding: Static method cannot be overriding in Java because their method calls are resolved at compile time but it didn't prevent you from declaring method with same name in sub class. In this case we say that method in sub class has hided static method from parent class. If you have a case where variable of Parent class is pointing to object of Child class then also static method from Parent class is called because overloading is resolved at compile time.

=======
Can you override static methods in java: No, you can not override static methods in java. Static methods belongs to class level not at object level.You can create static method with same name in child class and it won’t give you compilation error but it is called method hiding. You won’t get overriding behavior with it.

=======
Can you override private methods in java: No, you can not override private methods in java. Private methods are not visible to child class, hence you can not override it, you can only hide it.

=======
An inner class can use all the methods and variables of the outer class, even the private ones. The inner class gets to use these variables and methods just as if the methods and variables were declared within the inner class. An inner class instance must be tied to specific outer object on the heap.

=======
Inner class: As a member of its enclosing class, a nested class can be declared private, public, protected, or package private(default). These can only be declared in the top level class and top level class can't be declared as static or private.

=======
Where should you use nested class or benefits?
1) If a class is useful to only one class, it makes sense to keep it nested and together. It helps in packaging of the classes.
2) Java inner classes implements encapsulation. Note that inner classes can access outer class private members and at the same time we can hide inner class from outer world.
3) Keeping the small class within top-level classes places the code closer to where it is used and makes code more readable and maintainable.

=======
There are four types of inner classes: Nested Inner class, Method Local Inner class, Anonymous Inner class, Static inner class 

=======
You cannot have static method or variables inside the inner and anonymous class because inner class is implicitly associated with an object of its outer class so it cannot define any static method for itself. It will give compile time error. But you can have static method or variable inside the static inner classes.
- You can have static final member variables inside the inner class.
- You cannot mark local variables as public or static 

=======
Using private variables of outer class
class Outer_Demo {
   // private variable of the outer class
   private int num = 175;  
   // inner class
   public class Inner_Demo {
      public int getNum() {
         System.out.println("This is the getnum method of the inner class");
         return num;
      }
   }
}
Outer_Demo outer = new Outer_Demo();
// Instantiating the inner class
Outer_Demo.Inner_Demo inner = outer.new Inner_Demo();
System.out.println(inner.getNum());

=======
Method-local Inner class: we can write a class within a method and this will be a local type. Like local variables, the scope of the inner class is restricted within the method. A method-local inner class can be instantiated only within the method where the inner class is defined. The following program shows how to use a method-local inner class. You cannot have static method in local inner class.
public class Outerclass {
   // instance method of the outer class 
   void my_Method() {
      int num = 23;
      // method-local inner class
      class MethodInner_Demo {
         public void print() {
            System.out.println("This is method inner class "+num);	   
         }   
      } // end of inner class
	    // Accessing the inner class
      MethodInner_Demo inner = new MethodInner_Demo();
      inner.print();
   } 
   public static void main(String args[]) {
      Outerclass outer = new Outerclass();
      outer.my_Method();	   	   
   }
}

=======
Can the method local inner class object access method’s local variables: No, a method local inner class object can not access the method local variable. The local variables are not guaranteed to live as long as the local inner class object. The method local variable live on stack and exist only till the method lives, their scope is limited only code inside the method they are declared in. But the local inner class object created within the method lives on heap and it may exist even after the method ends if in case the reference of this local inner class is passed into some other code and is stored in an instance variable. So we can not be sure that the local variables will live till the method local inner class object lives, therefore the method local inner class object can not access the method local variable. To access the method local variables, the variable has to be declared as final.

=======
Where is the local final variable in method stored
class Employee {
  public void getAddress(){
    final int location = 13; 
    int notFinalVar = 13;   
    class Address {
       System.out.println (location); 
       System.out.println (notFinalVar); // compiler error
    }
} Stack. All local variable (final or not) stored into the stack and go out of scope when the method execution is over. But about final variable JVM take these as a constant as they will not change after initiated . And when a inner class try to access them compiler create a copy of that variable (not that variable it self) into the heap and create a synthetic field inside the inner class so even when the method execution is over it is accessible because the inner class has it own copy. So does it finally means that final variables are stored in finally Stack memory Area? final variable also stored in stack but the copy that variable which a inner class have stored in heap.

======
Synthetic Fields: Synthetic field are filed which actually doesn't exist in the source code but compiler create those fields in some inner classes to make those field accessible. In simple word hidden field.

======
Can a method local inner class access the local final variables? Why: Yes. Because the final variables are stored on heap and live as long as the method local inner class object may live.

========
Anonymous Inner class: An inner class declared without the name is called Anonymous Inner class. In this case we declare and instantiate them at the same time. 
abstract class AnonymousInner {
   public abstract void mymethod();
}
public class Outer_class {
   public static void main(String args[]) {
      AnonymousInner inner = new AnonymousInner() {
         public void mymethod() {
            System.out.println("This is an example of anonymous inner class");
         }
      };
      inner.mymethod();	
   }
}

=======
Anonymous Inner Class as Argument
interface Message {
   String greet();
}
public class My_class {
   // method which accepts the object of interface Message
   public void displayMessage(Message m) {
      System.out.println(m.greet() + ", This is an example of anonymous inner class as an argument");  
   }
   public static void main(String args[]) {
      // Instantiating the class
      My_class obj = new My_class();
      // Passing an anonymous inner class as an argument
      obj.displayMessage(new Message() {
         public String greet() {
            return "Hello";
         }
      });
   }
}

=======
Can an anonymous class define method of its own: Yes. But there will be no way by which the methods defined in the anonymous class which are not present in its superclass be invoked. As only those methods which are defined in the superclass which the anonymous class extends be invoked defining the methods in the anonymous class will be of no use.

=======
You can create an anonymous class of any class. No need to have the abstract or interface. You are just overriding the methods. It is just like creating a subclass without a name.
class Demo {
   void show() {
      System.out.println("i am in show method of super class");
   }
}
class Flavor1Demo {
   //  An anonymous class with Demo as base class
   static Demo d = new Demo() {
       void show() {
           super.show();
           System.out.println("i am in Flavor1Demo class");
       }
   };
   public static void main(String[] args){
       d.show();
   }
}

======
Can a method which is not in the definition of the superclass of an anonymous class be invoked on that anonymous class reference? No. Compilation will fail. As the reference variable type of the anonymous class will be of superclass which will not know of any method defined inside the anonymous class the compilation will fail.
class SuperClass {
  void doSomething() {
    System.out.println("In the Super class");
  }
}
SuperClass anon = new SuperClass(){
  void doSomething() {
    System.out.println("In the Anonymous class");
  }
  void doStuff() {
    System.out.println("An Anonymous class method not present in superClass");
  }
}
public void doIt(){
	anon.doSomething(); // legal superClass has this method
	anon.doStuff(); // Not legal 
}

=======
Static Nested class: is a nested class which is a static member of the outer class. It can be accessed without instantiating the outer class, using other static members. Just like static members, a static nested class does not have access to the instance variables and methods of the outer class. Static nested classes can access only static members of the outer class. 
public class Outer {
   static class Nested_Demo {
      public void my_method() {
         System.out.println("This is my nested class");
      }
   }
   public static void main(String args[]) {
      Outer.Nested_Demo nested = new Outer.Nested_Demo();	 
      nested.my_method();
   }
}

======
Generics allow type (Integer, String, …etc and user defined types) to be a parameter to methods, classes and interfaces. For example, classes like HashSet, ArrayList, HashMap, etc use generics very well. We can use them for any type.

======
Advantage of Java Generics
1)	Type-safety : We can hold only a single type of objects in generics. It doesn’t allow to store other objects.
2)	Type casting is not required: There is no need to typecast the object.
3)	Compile-Time Checking: It is checked at compile time so problem will not occur at runtime. The good programming strategy says it is far better to handle the problem at compile time than runtime.

======
Generics was added in Java 5 to provide compile-time type checking and removing risk of ClassCastException that was common while working with collection classes. The whole collection framework was re-written to use generics for type-safety. 
List list = new ArrayList();
list.add("abc");
list.add(new Integer(5)); //OK
for(Object obj : list){
	//type casting leading to ClassCastException at runtime
    String str=(String) obj; 
}

======
public class GenericsType<T> {
	private T t;
	public T get(){
		return this.t;
	}
	public void set(T t1){
		this.t = t1;
	}
	public static void main(String args[]){
		GenericsType<String> type = new GenericsType<>();
		type.set("Pankaj"); //valid	
		GenericsType type1 = new GenericsType(); //raw type
		type1.set("Pankaj"); //valid
		type1.set(10); //valid and autoboxing support
	}
}
Notice the use of GenericsType class in the main method. We don’t need to do type-casting and we can remove ClassCastException at runtime. If we don’t provide the type at the time of creation, compiler will produce a warning that “GenericsType is a raw type. References to generic type GenericsType<T> should be parameterized”. When we don’t provide type, the type becomes Object and hence it’s allowing both String and Integer objects but we should always try to avoid this because we will have to use type casting while working on raw type that can produce runtime errors.

======
Bound parameter: To declare a bounded type parameter, list the type parameter’s name, followed by the extends keyword, followed by its upper bound, similar like below method.
public static <T extends Comparable<T>> int compare(T t1, T t2){
	return t1.compareTo(t2);
}
The invocation of these methods is similar to unbounded method except that if we will try to use any class that is not Comparable, it will throw compile time error. Bounded type parameters can be used with methods as well as classes and interfaces. Java Generics supports multiple bounds also, i.e <T extends A & B & C>. In this case A can be an interface or class. If A is class then B and C should be interfaces. We can’t have more than one class in multiple bounds.

======
We know that Java inheritance allows us to assign a variable A to another variable B if A is subclass of B. So we might think that any generic type of A can be assigned to generic type of B, but it’s not the case. Lets see this with a simple program.
public class GenericsInheritance {
	public static void main(String[] args) {
		String str = "abc";
		Object obj = new Object();
		obj = str; // works because String is-a Object, inheritance in java
		MyClass<String> myClass1 = new MyClass<String>();
		MyClass<Object> myClass2 = new MyClass<Object>();
		// myClass2 = myClass1; // compilation error since MyClass<String> is not a MyClass<Object>
		obj = myClass1; // MyClass<T> parent is Object
	}
	public static class MyClass<T>{}
}
We are not allowed to assign MyClass<String> variable to MyClass<Object> variable because they are not related, in fact MyClass<T> parent is Object.

======
Upper bounded wild-cards are used to relax the restriction on the type of variable in a method. Suppose we want to write a method that will return the sum of numbers in the list, so our implementation will be something like this.
public static double sum(List<Number> list){
	double sum = 0;
	for(Number n : list){
		sum += n.doubleValue();
	}
	return sum;
}
Now the problem with above implementation is that it won’t work with List of Integers or Doubles because we know that List<Integer> and List<Double> are not related, this is when upper bounded wildcard is helpful. We use generics wildcard with extends keyword and the upper bound class or interface that will allow us to pass argument of upper bound or it’s subclasses types. The above implementation can be modified like below program.
public class GenericsWildcards {
	public static void main(String[] args) {
		List<Integer> values = new ArrayList<>();
		values.add(3); values.add(5); values.add(10);
		double sum = sum(values);
		System.out.println("Sum of values="+sum);
	}
	public static double sum(List<? extends Number> list){
		double sum = 0;
		for(Number n : list){
			sum += n.doubleValue();
		}
		return sum;
	}
}
It’s similar like writing our code in terms of interface, in above method we can use all the methods of upper bound class Number. Note that with upper bounded list, we are not allowed to add any object to the list except null. If we will try to add an element to the list inside the sum method, the program won’t compile.

======
If you have a class hierarchy A, B is a subclass of A, and C and D both are subclass of B like below
class A {}
class B extends A {}
class C extends B {}
class D extends B {}
Then
List<? extends A> la;
la = new ArrayList<B>();
la = new ArrayList<C>();
la = new ArrayList<D>();
List<? super B> lb;
lb = new ArrayList<A>(); //fine
lb = new ArrayList<B>(); //fine
lb = new ArrayList<C>(); //will not compile

public void someMethod(List<? extends B> lb) {
    B b = lb.get(0); // is fine
    lb.add(new C()); //will not compile as we do not know the type of the list, only that it is bounded above by B
}
public void otherMethod(List<? super B> lb) {
    B b = lb.get(0); // will not compile as we do not know whether the list is of type B, it may be a List<A> and only contain instances of A
    lb.add(new B()); // is fine, as we know that it will be a super type of A 
}
A bounded wildcard is like ? extends B where B is some type. That is, the type is unknown but a "bound" can be placed on it. In this case, it is bounded by some class, which is a subclass of B.

=======
Java Stack: is part of your computer’s memory where temporary variables, which are created by all functions you do, are stored. It is used to execute a thread and may have certain short-lived values as well as references to other objects. When a method is invoked, it creates a new block in the stack for that particular method. The new block will have all the local values, as well as references to other objects that are being used by the method. The memory size of a Java stack is generally much less than in a Java heap space because when a method ends, all the variables created on the stack are erased forever.
1) The size of the stack will vary as methods and functions create and delete local variables as needed.
2) Memory is allocated and then subsequently freed without you needing to manage the memory allocation.
3) Stack has size limits, which can vary according to the operating system you use.
4) Variables that are stored on the stack exist for as long as the function that created them are running.

=======
Java Heap: Java objects are stored in an area, which is called the heap. It is created when the program is run, and its size may decrease or increase as your program runs. It can easily become full, and when it does, garbage collection is initiated. This is when objects that are no longer used are deleted to make way for new objects. Unlike in a Java stack where memory allocation is done when your program is compiled, in a heap it is allocated as your program is run. Accessing variables placed here is a bit slower compared to a stack’s direct and fast access.   
1) Memory is not managed automatically nor is it as tightly managed by the central processing unit the way stack is managed. You would need to free allocated memory yourself when these blocks are no longer needed.
2) The heap is prone to memory leaks, where memory is allocated to unused objects and will not be available to processes other than that.
3) There is no size limit in the heap.
4) Compared to stack, objects in the heap are much slower to access. It is also slower to write to the memory on the heap.

===============
Externalization
===============
What is Externalization in Java: In serialization, the Java Virtual Machine is totally responsible for the process of writing and reading objects. This is useful in most cases, as the programmers do not have to care about the underlying details of the serialization process. However, the default serialization does not protect sensitive information such as passwords and credentials. Thus externalization comes to give the programmers full control in reading and writing objects during serialization.

======
The Externalizable Interface: When you want to control the process of reading and writing objects during the serialization and de-serialization process, have the object’s class implemented the java.io.Externalizable interface. Then you implement your own code to write object’s states in the writeExternal() method and read object’s states in the readExternal() method. Unlike Serializable interface which will serialize the variables in object with just by implementing interface, here we have to explicitly mention what fields or variables you want to serialize. Serializable uses reflection to construct object and does not require no arg constructor. But Externalizable requires public no-arg constructor.

======
Example implementing the Externalizable interface
public class User implements Externalizable {
    // attributes
    // methods
    // externalization methods:
    public void writeExternal(ObjectOutput out) {
        // implement your own code to write objects of this class
    }
    public void readExternal(ObjectInput in) {
        // implement your own code to read serialized objects of this class
    }
}
For more: https://www.codejava.net/java-se/file-io/understanding-java-externalization-with-examples

=================
MARKER INTERFACE
=================
It is an empty interface (no field or methods). Examples of marker interface are Serializable, Cloneable and Remote interface. All these interfaces are empty interfaces.
public interface Serializable {
  // nothing here
}
Examples of Marker Interface which are used in real-time applications :
- Cloneable interface : Cloneable interface is present in java.lang package. There is a method clone() in Object class. A class that implements the Cloneable interface indicates that it is legal for clone() method to make a field-for-field copy of instances of that class. Invoking Object’s clone method on an instance of the class that does not implement the Cloneable interface results in an exception CloneNotSupportedException being thrown. By convention, classes that implement this interface should override Object.clone() method.
- Serializable interface : Serializable interface is present in java.io package. It is used to make an object eligible for saving its state into a file. This is called Serialization. Classes that do not implement this interface will not have any of their state serialized or de-serialized. All subtypes of a serializable class are themselves serializable.
- Remote interface : Remote interface is present in java.rmi package. A remote object is an object which is stored at one machine and accessed from another machine. So, to make an object a remote object, we need to flag it with Remote interface. Here, Remote interface serves to identify interfaces whose methods may be invoked from a non-local virtual machine.Any object that is a remote object must directly or indirectly implement this interface.
