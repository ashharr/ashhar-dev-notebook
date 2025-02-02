## JAVA 8 Features

1.Functional Interfaces

2.Lambda Expressions

3.Default Methods in Interfaces

4.Static Methods in Interfaces

5.Predefined Interfaces

6.Method Reference ,Constructor Reference

7.Stream API

8.Date and Time API

9.Optional Class

## Functional Programming

From Java 8 Version ,Using Functional Programming we can pass a function as an argument to a method

    class Calculator{

    static void evaluate(Addition a ){

    a.add(10,20);

    }

    Addition addNumbers =(a,b)-(a+b); Functional Programming

    System.out.println(addNumbers.add(1,2));

**Definition of Functional Interface:**

Only one abstract method in interface is called Functional Interface.

Examples of Functional Interface :

Comparable

Comparator

Runnable

Callable

**Why Functional Interface**

- Functional Interface is used for enabling Functional Programming in Java.
- Functional Interface is also used for defining Lambda Expressions to pass a function directly as an argument.

        @FunctionalInterface
        interface Addition(){

        void add(int a ,int b);
 
        void add(int a, int b ,int c); ----- compiler will start throwing error , only one abstract method should be there
       
      }


**@FunctionInterface**

@FunctionInterface is a marker annotation to mark the interface as a functional Interface explicitly

Two ways of creating Functional Interface

1.Creating as Effective Functional Interface

2.Forcing it to be a Functional Interface

**Annonymous Inner Class:**

i.e Inner Class without Name , only one time use (instant use)

## LAMBDA EXPRESSIONS

- It is an anonymous function without name, return type and modifiers.
- To enable functional programming
- By using “--”

    
        public int getSum(int a ,int b){

        System.out.println(a+b);

        }

        ()-System.out.println(“Java Programming”);

        (int a ,int b)- System.out.println(a+b);

## Default Method in Interfaces

Default method came into picture for solving limitation of interfaces. For adding more functionality methods in interface without breaking the implementation classes functionality.

    interface Example{
    abstract void m1();
    abstract void m2();
    }

    class Sample implements Example{ 
    public void m1(){
    }
    }

    class Demo implements Example
    {
    public void m1(){
    }
    }

Since there is no implementation of m2() method in both classes ,compiler throws error. So, in java 8 concept of default method is introduced.

     interface** Example{
     abstract **void** m1();
     default **void** m2(){
    }
    }

* Default methods of an interface are the concrete methods for which implementing classes need not to give implementation. They inherit default implementation.
* Default methods are introduced to add extra features to current interfaces without disrupting their existing implementations. 
* For example, stream() is a default method which is added to Collection interface in Java 8. 
* If stream() would have been added as abstract method, then all classes implementing Collection interface must have implemented stream() method which may have irritated existing users.
* To overcome such issues, default methods are introduced to interfaces from Java 8.


To solve the diamond problem, Java 8 proposes 3 rules to follow. They are,

Rule 1 : Select classes over interfaces

If your class inherit multiple methods with same signature then a method from super class is selected (Remember a class can inherit only one class).

Rule 2 : Select most specific interfaces than general interfaces.

If your class doesn’t extend any class and inherit multiple methods with same signature from multiple interfaces which belong to same hierarchy, then a method from most specific interface is selected.

Rule 3 : InterfaceName.super.methodName()

If your class doesn’t extend any class and inherit multiple methods with same signature from multiple interfaces which doesn’t belong to same hierarchy, then override that method and from within body explicitly call desired method as InterfaceName.super.methodName()

## Static Method in Interfaces

Q. What is the purpose of introducing static methods in java interface ?

Java interface static methods are good for providing utility methods, for example null check, collection sorting etc. Java interface static method helps us in providing security by not allowing implementation classes to override them.

Q. What will happen if I override static method ?

Try to add @Override annotation to the method, it will result in compiler time error.

Q. Is it possible to have multiple static methods in an interface?

Yes,

    interface Example
    {
     static public boolean isNull(String input)
    {

        if(input!=null){return false;
        }
        return true;

    } 
    }    
     public class Sample {
     public static void main(String[] args) {
        System.out.println (Example.isNull("ok"));
    }  
    }


 
## Predefined Interfaces

1.Predicate

2.Function

3.Consumer

4.Supplier

Two Argument Predefined Functional Interface:

1.BiPredicate

2.BiFunction

3.BiConsumer

Predicate:

Conditional checks

Input

Boolean is return type.

test()

      String[] res={"ashhar","General","sai"};
      Predicate<String employeePredicate=e-e.length()>4;
      for(String s1:res){if(employeePredicate.test (s1))
      {
      System.out.println (s1);
      }
      }

Function:

Input and Output

Output type is return type.

apply()

    Function<String,Integer function=fn-fn.length ();
    System.out.println(function.apply("durga"));

Consumer:

Input

Void is return type

Accept()

       Consumer<String consumer=cn-System.out.println (cn);
       consumer.accept ("Capgemini");

        Consumer<Employee emp1=emp123-{
        System.out.println (emp123.getEmpName ());
        System.out.println (emp123.getEmpId ());
        };
        for(Employee employee:employeeList){
        emp1.accept(employee);
        }

Supplier:

It does not require any input , but returns output.

get()

      Supplier<Date date=()-**new** Date ();
      System.out.println (date.get ());

//otp generation

       Supplier<String otp=()-{
       String otp1="";
       for(int i=0;i<=6;i++){
       otp1=otp1+(int)(Math.random ()10);
       }
       return otp1;
       };
       System.out.println (otp.get ());

## Method and Constructor Reference

- Method Reference and Constructor Reference is alternative to Lambda Expressions.
- Method Reference is used for Code Reusability
- A short end way of writing a lambda expression that will refer to the existing method.
- ::--- Method Reference Operator

Types of Method References:

1.Static Method Reference --- className::method name

2.Instance Method Reference --- object reference :: method name

3.Constructor Reference --- className :: new

If the method returns object ,then we should use constructor reference.

     public interface FunctionalInterface {
     void add(int x,int y);
     }

        public class Test {void add(int x,int y){
        System.out.println (x+y);
        }

        public class MR {public static void main(String[] args) {
        Test t1=new Test ();
        FunctionalInterface function1 =t1::add;
        function1.add (10,20);
        }
        }

Constructor Reference:

    public interface FunctionalInterface {
    public Test get();
    }

        class Test {
        Test(){
        System.out.println ("hello");
        }
        }

        public class MR {public static void main(String[] args) {
        FunctionalInterface f=Test::new;
        Test s=f.get ();
        }
        }

  Wherever fn interface , we can use lambda expressions

  Function<String,Intgeger f =s-s.length
  
## STREAM API 
[STREAM API QUESTIONS](https://ashhar-dev-notebook.netlify.app/stream%20api/streamapi/)

## DATE AND TIME API

 * java.time package
 * LocalTime ,LocalDate,LocalDateTime ,ZonedDateTime, Period ,Duration.

old and new java 8 existing date/time api's

 * Thread Safety

 * Api's design and understanding 

 * Timezone handling.


Local Date, Local Time and LocalDateTime:
java.util.date,java.util.timestamp, java.util.calender only for basic operations.

java.util.time package , it is loosely based and the library is joda-time api.


    LocalDate date = LocalDate.now();  ---> 2023-06-02.
    LocalDate date1 = LocalDate.of(2023,06,02);
    LocalDate date2 = LocalDate.parse("2023-06-02");
    LocalDate date3 =date2.plusDays(1);  --> 2023-06-03
    boolean isBefore = LocalDate.parse("2023-06-02").isBefore(LocalDate.parse("2023-06-03");
    boolean isAfter = LocalDate.parse("2023-06-02").isAfter(LocalDate.parse("2023-06-03");


    LocalTime now = LocalTime.now();
    LocalTime now1 = LocalTime.of(6,30);
    LocalTime now2 = LocalTime.parse("6:30");

    LocalDateTime time = LocalDateTime.now();
    LocalDateTime time1 = LocalTime.parse(" 2023-06-02T6:30:45");
    LocalDate date4 = LocalDateTime.now().toLocalDate();

    ZoneId zoneId = ZoneId.of("Asia/Kolkatta");
    ZonedDateTime dateTime =  ZonedDateTime.of(LocalDateTime.now(),zoneId);

    int duration = Duration.between(LocalTime.of(6,30),LodalTime.of(6,29)).getSeconds();   

    LocalDateTime dataTime = LocalDateTime.of(2015,Month.JANUARY,25,6,30);
    String format = LocalDateTime.format(DateTimeFormatter.ISO_DATE);
    LocalDateTime dateTime1 =  dateTime.format(DateTimeFormatter.ofPattern("dd/MM/yyyy"));



## Optional Class

* Optional is final class in java 8.
* To handle values as 'available' or 'not available' instead of checking null values.

Different ways to create an optional object.

1.Optional.empty()

2.Optional.of()

3.Optional.ofNullable()

Optional.empty(): This method returns an empty optional object, indicating that it doesn't contain any value. It is often used to initialize an optional object when you know it should be empty. For example:


    Optional<String> emptyOptional = Optional.empty();

Optional.of(value): This method creates an optional object that contains a non-null value. It throws a NullPointerException if the provided value is null. For example:

     String name = "John";

     Optional<String> optionalName = Optional.of(name);

Optional.ofNullable(value): This method creates an optional object that contains a value, which can be null. If the provided value is null, it returns an empty optional. If the value is non-null, it creates an optional containing that value. This method is useful when you are not certain if the value can be null. For example:


      String city = null;

      Optional<String> optionalCity = Optional.ofNullable(city);

In summary, Optional.empty() creates an empty optional, Optional.of(value) creates an optional with a non-null value, and Optional.ofNullable(value) creates an optional that may or may not contain a value (even if the value is null).

*To get value from optional object we can use get() method

    System.out.println(optionalName.get());


4.ifPresent (consumer)
   If a value is present , it invokes the specified consumer with the value, otherwise does nothing.
    
     optionalName.ifPresent(s-> System.out.println(s.toUpperCase());

5.orElse()
    Returns the value if present ,otherwise returns other value.
  
    Optional<String> empty = Optional.empty();
   
     System.out.println(empty.orElse("default"));

6.orElseGet (supplier)
   Returns the value if present , otherwise invokes the supplier.
   
     Optional<Date> emptyDate=Optional.empty();
   
     System.out.println(emptyDate.orElseGet()->new Date());

7.orElseThrow (supplier)
  Returns the contained value, if present, otherwise throws an exception to be created by the provided supplier.
  
     emptyDate.orElse(InvalidDateException:: new);
  


