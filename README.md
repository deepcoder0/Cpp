C, C++ &amp; OOPS for Interviews

# Introduction
● Object-Oriented Programming is a methodology or paradigm to design a program using classes and objects. It simplifies the software development and maintenance by providing some concepts defined below :
● Class is a user-defined data type which defines its properties and its
functions. Class is the only logical representation of the data. For example, Human being is a class. The body parts of a human being are its properties, and the actions performed by the body parts are known as functions. The class does not occupy any memory space till the time an object is instantiated.

Object is a run-time entity. It is an instance of the class. An object can
represent a person, place or any other item. An object can operate on both data members and member functions.

###### Note : When an object is created using a new keyword, then space is allocated for the variable in a heap, and the starting address is stored in the stack memory. When an object is created without a new keyword, then space is not allocated in the heap memory, and the object contains the null value in the stack.

# Features of OOP


- **Abstraction**
We try to obtain abstract view, model or structure of real life problem, and reduce its unnecessary details. With definition of properties of problems, including the data which are affected and the operations which are identified, the model abstracted from problems can be a standard solution to this type of problems. It is an efficient way since there are nebulous real-life problems that have similar properties.

- **Encapsulation**
Encapsulation is the process of combining data and functions into a single unit called class. In Encapsulation, the data is not accessed directly; it is accessed through the functions present inside the class. In simpler words, attributes of the class are kept private and public getter and setter methods are provided to manipulate these attributes. Thus, encapsulation makes the concept of data hiding possible. (Data hiding: a language feature to restrict access to members of an object, reducing the negative effect due to dependencies. e.g. "protected", "private" feature in C++).

- **Inheritance**
The idea of inheritance is simple, a class is based on another class and uses data and implementation of the other class. And the purpose of inheritance is Code Reuse.

- **Polymorphism**
Polymorphism is the ability to present the same interface for differing underlying forms (data types). With polymorphism, each of these classes will have different underlying data. A point shape needs only two coordinates (assuming it's in a two-dimensional space of course). A circle needs a center and radius. A square or rectangle needs two coordinates for the top left and bottom right corners and (possibly) a rotation. An irregular polygon needs a series of lines.




**OOPS - SYNTAX**
```cpp
#include<iostream>
using namespace std;

class Student {
   // By default all properties of class are PRIVATE;
   // So we have to make them PUBLIC to access them outside the class

   public:  
      int rollNumber;
      int age;

   private:
      int marks;

   public:

   // GETTERS AND SETTERS :-> used to access and modify private members
   int getAge() {
      return age;
   }
   void setAge(int a) {
      age = a;
   }


};

int main() {
   // Creating an object
   Student s1; // Statically created object

   Student *s2 = new Student; // Dynamically created object
   // simlar to how we create other data types Dynamically int *a = new int

   // setting values for properties og object created statically
   s1.name = Deep
   s1.age = 10;

   // setting values for properties og object created Dynamically
   (*s2).name = "Priya"; // or s2 -> name = "Priya"
   (*s2).age = 20; // or s2 -> age = 20

}

```
# Constructors
● Constructor : Constructor is a special method which is invoked automatically at the time of object creation. It is used to initialize the data members of new objects generally. The constructor in C++ has the same name as class or structure.
There can be two types of constructors in C++.
1. Default constructor :  A constructor which has no argument is known as default constructor. It is invoked at the time of creating an object.

2. Parameterized constructor : Constructor which has parameters is called a parameterized constructor. It is used to provide different values to distinct objects.

3. Copy Constructor : A Copy constructor is an overloaded
constructor used to declare and initialize an object from another object. It is of two types - default copy constructor and user defined copy constructor.

###### DEFAULT CONSTRUCTOR
-> Exactly same name to class
-> No return type
-> No input arguments
-> As soon as we create the class this constructor is automatically created.
-> For every object in its lifetime constructor is called only ONCE.

```cpp
#include<iostream>
using namespace std;
class Student {
   public:  
      int rollNumber;
   private:
      int age;
   public:
   // Sooner we create our own constructor; either Parameterized or not;
   // then default constructor will not be called, ours will be called.

   Student() {
      cout<<'Constructor called!'<<endl;
      // If we remove this constructor code and only parameterised constrictors are present,
      // than creating an object w/o paameters with give us an error.
   }

   // Parameterized Constructors
   Student(int r) {
      rollNumber = r;
   }

   Student(int r, int a) {
      rollNumber = r;
      age = a;
   }
};

int main() {
   Student s1; // its like s1.Student() ; Constructor as a function is called.
   Student s1(10)
   Student *s2 = new Student(10);  
}
```

**THIS keyword**
In C++ programming, this is a keyword that refers to the current instance of the class. There can be 3 main usage of this keyword in C++.

1.) It can be used to pass current object as a parameter to another method.
2.) It can be used to refer current class instance variable.
3.) It can be used to declare indexers.

```cpp
class Student {
   public:  
      int rollNumber;
   private:
      int age;
   public:
      //Constructor with 2 parameters.
   Student(int rollNumber, int age) {
      // this -> holds address of current Object
      this.rollNumber = rollNumber; // or this -> age = age;
      this.age = age;
   }
};
int main() {
   Student s1;
   Student s1(10, 101)
   Student *s2 = new Student(11, 110);  
}
```

# Copy Constructor
Creating an object2 that has same properties to some object1 that is already created.

```cpp
Student object2(object1); // obj1-Static and obj2-Static
Student object2(*object1); // obj1-dynamic and obj2-Static
Student *object2 = new Student(object1); // obj1-Static and obj2-Dynamic
Student *object2 = new Student(*object1); // obj1-dynamic and obj2-dynamic
```
This is similar to s2.Student(s1)
This means that default constructor can also take object as a parameter.

**Copy Assignment Operator(=)**
Can only be used when both object are already created.And you need to update values of a object.
```cpp
object2 = object1;
//This refers to
object2.age = object1.age;
```

```cpp
int main(){
   Student s1;   // Constructor 1 called
   Student s2(10);   // Constructor 2 called
   Student s3(10,100);   // Constructor 3 called
   Student s4(s3);   // Copy Constructor called
   s1 = s2;     //Copy Assignment operator

   //Special Case
   Student s5 = s4;

   // this is something Like
   Student s5;
   s5 = s4;
   // Hence copy assignment operator must be used;?

   // BUT NO
   // This is treated by the compiler as
   Student s5(s4); // USING COPY CONSTRUCTOR
}
```

![Copy-Constructor vs Copy Assignment Operator](https://i.postimg.cc/kgnc0kHt/image.png)


# Destructors
Destructor : Adestructor works opposite to constructor; it destructs the objects of classes. It can be defined only once in a class. Like constructors, it is invoked automatically. A destructor is defined like a constructor. It must have the same name as class, prefixed with a tilde sign (~).
**NOTE**
Destructor for dynamically created object is not automatically called . WHY ?
Because at that location, object address is kept;  so to delete dynamically created object we need to ourselves use ```delete objectName; ```
No we will see destructor is called.

# Shallow And Deep Copy

Default copy constructor only does shallow copy, i.e., a member by member copy.
Student s2(s1); is shallow copy.

![deep-copy-shallow-copy](https://i.stack.imgur.com/AWKJa.jpg)


```cpp
class Student {
   int age;
   int *name;

public:

Student(int age, char name){
   // For just age, an int variable there is no shallow/deep copy!
   this -> age = age;

   // SHALLOW COPY
   this -> name = name;

   // DEEP COPY
   this -> name = new char[strlen(name) + 1];
   strcpy(this -> name, name)
}

void display(){
   cout << this.name << this.age << endl;
}
};
int main(){
   char name[] = "abcd";
   Stident s1(20, name);
   s1.display();
}
```

# Initialisation List
LOREN IPSUM

# Constant Object and Functions
**const Student s1;**

We can't change any property of s1 now.
Compiler do not let you call Any function through const object.(Not even getters and setters.) -> Error will pop up.

We can only access constant Functions: Functions that do not change any value in their codes.

How to mark a function constant?
**int functionName() const {}**

If you mark a setter function constant, then compiler will call that function but you will get error when value of a constant var will be required to get changed.

# Static members

**Static Properties**

-Members which belongs to the class and there is no need to create a copy again and again.
-Every object will get a same copy.
-By default properties are no static.
-Static members has no access to this pointers.

```cpp
class Student {
   public:

   int r_num;
   int age;

   static int totalStudents; // total number of students present.
   // this property actually belongs to a class and not a personal for object.

   Student() {
      totalStudents ++;
   }

};

int main() {
   // To access a static member or a property which is of class
   cout << Student :: totalStudents << endl;
   // This is done using Scope resolution operator(::).

   // Initialisation
   int Student :: totalStudents = 0;

   // What if you access object.totalStudent ? Error will not come !
   // But this is logically incorrect

   // What is you change static property using object then that can be changed and will be changed for complete class.
   // (Because that change will happen inside the class.)

}
```

**Static Functions**
That function will not be dependant on the object; Its a function of the class.

```cpp
class Student {
   static int totalStudents;
   public:
   int r_num;
   int age;

   Student() {
      totalStudents ++;
   }
   static int getTotalStudents() {
      return totalStudents;
   }
};
int main() {
   Student s1
   cout << Student :: getTotalStudents() << endl;
}
```

# Operator overloading
Changing property of pre-existing operator as per our use.
Operator overloading is a compile-time polymorphism in which the operator is overloaded to provide the special meaning to the user-defined data type. Operator overloading is used to overload or redefines most of the operators available in C++. It is used to perform the operation on the user-defined data type. For example, C++ provides the ability to add the variables of the user-defined data type that is applied to the built-in data types.

```cpp
// COMPLETE FRACTION CLASS
class Fraction {
	private :
		int numerator;
		int denominator;
	public :
		Fraction(int numerator, int denominator) {
			this -> numerator = numerator;
			this -> denominator = denominator;
		}
		void print() {
			cout << this -> numerator << " / " << denominator << endl;
		}
		void simplify() {
			int gcd = 1;
			int j = min(this -> numerator, this -> denominator);
			for(int i = 1; i <= j; i++) {
				if(this -> numerator % i == 0 && this -> denominator % i == 0) {
					gcd = i;
				}
			}
			this -> numerator = this -> numerator / gcd;
			this -> denominator = this -> denominator / gcd;
		}

		Fraction add(Fraction const &f2) {
			int lcm = denominator * f2.denominator;
			int x = lcm / denominator;
			int y = lcm / f2.denominator;

			int num = x * numerator + (y * f2.numerator);

			Fraction fNew(num, lcm);
			fNew.simplify();
			return fNew;
		}
      // Addition using Operator Overloading
		Fraction operator+(Fraction const &f2) const {
			int lcm = denominator * f2.denominator;
			int x = lcm / denominator;
			int y = lcm / f2.denominator;

			int num = x * numerator + (y * f2.numerator);

			Fraction fNew(num, lcm);
			fNew.simplify();
			return fNew;
		}
      // Multiplicatiion using Operator Overloading
		Fraction operator*(Fraction const &f2) const {
			int n = numerator * f2.numerator;
			int d = denominator * f2.denominator;
			Fraction fNew(n, d);
			fNew.simplify();
			return fNew;
		}
      // Boolean using Operator Overloading
		bool operator==(Fraction const &f2) const {
			return (numerator == f2.numerator && denominator == f2.denominator);
		}
      // We have market overloading function as constant functions becauuse they do not change in the properties of objects.
		void multiply(Fraction const &f2) {
			numerator = numerator * f2.numerator;
			denominator = denominator * f2.denominator;
			simplify();
		}
};

#include <iostream>
using namespace std;
int main() {
	Fraction f1(10, 2);
	Fraction f2(15, 4);
	Fraction f3 = f1.add(f2);
	Fraction f4 = f1 + f2;
	Fraction f5 = f1 * f2;
}
```

# Encapsulation
Clubbing properties/data and functions in a block is encapsulation. Can be done with the help of classes.

# Abstraction
**Hiding** the unnecessary details.

# Inheritance

Encapsulation
Encapsulation is the process of combining data and functions into a single unit called class. In Encapsulation, the data is not accessed directly; it is accessed through the functions present inside the class. In simpler words, attributes of the class are kept private and public getter and setter methods are provided to manipulate these attributes. Thus, encapsulation makes the concept of data hiding possible.

Abstraction
We try to obtain an abstract view, model or structure of a real life problem, and reduce its unnecessary details. With definition of properties of problems, including the data which are affected and the operations which are identified, the model abstracted from problems can be a standard solution to this type of problems. It is an efficient way since there are nebulous real-life problems that have similar properties

Advantages are mainly data hiding and error avoidance.

Data binding : Data binding is a process of binding the application UI and business logic. Any change made in the business logic will reflect directly to the application UI.

Inheritance
Inheritance is a process in which one object acquires all the properties and behaviors of its parent object automatically. In such a way, you can reuse, extend or modify the attributes and behaviors which are defined in other classes.
In C++ , the class which inherits the members of another class is called derived class and the class whose members are inherited is called base class. The derived class is the specialized class for the base class.

Access Modifiers Private: Only functions of same class
Public: Anyone
Protected: Only child classes can access, Not even by itself similat to private
Syntax:

class Vehicle{
private:
int maxSpeed;

protected:  
    int numTyres;  

public:  
    string colour;
};

class Car : public Vehicle{
// private wont be inherited
// public will be public here
// protected will be protected
}
You can use and access properties just like they belong to the child class only , no extra keyword.

class Car : protected Vehicle{
// private wont be inherited
// public will be protected here
// protected will be protected
}

class Car : private Vehicle{
// private wont be inherited
// public will be private here
// protected will be private
}

if we dont mention access modifier, It is private by default

Constructors in inheritance

By default, parent class constructors get called when we create a variable of any child class.

If u make a constructor in any class, make sure u make a default constr too cz it will be called while object creation of child class.

How to make a parametrized constructor in child class?
Car(int x): Vehicle(x){
// that : Vehicle() is done by default if not mentioned for unparameterized constr.
}
and in vehicle class
Vehicle(int x){ this.x=x;
}

A class can only call constr of its immediate parent not granndparent.

Destrtuctors are called in reverse manner of constr. like child first then parent.

Types of Inheritance

Single Inher.
Multi level Inher.
Hirarchial Inher. : One inherited by many
Multiple Inher: Multiple parents
Syntax:
class Teacher{
public:
string name;
string age;
void print(){
print(teacher); } };
class Student{ public:
void print(){
print(Student);
}
};
class TA: public Teacher,public Student{
// constr of teacher will be called first cz written first,then Student
};
TA x; x.print(); // Error cz of ambiguity
x.Student:: print(); //Right way

if we have a print() in our class then only it will look above else just access our own object.

Hybrid Inher. : Combination of all example: Diamond shape

Order of calling constr.
vehicle
car->vehicle bus->vehicle
truck->car,bus

1-vehicle()
2-car()
3-vehicle()
4-bus()
5-truck()

Virtual Base Class

If we want just 1 copy of vehicle in above example ,we can use virtual class

vehicle
car->virtual vehicle bus->virtual vehicle
truck->car,bus

1-vehicle()
2-car()
3-bus()
4-truck()
// Vehicle() only called once

What virtual class means is we just give a pointer to class and not the actual class while inher.

If we make virtual inheritance , child class calls the constr of grand parent too unlike just of immediate parent before.Infact, in diamond inher prob, car, bus dont even call for the constr first, the truck obj calls the constr. we can check using parametrised constr..

Polymorphism
Polymorphism is the ability to present the same interface for differing underlying forms (data types). With polymorphism, each of these classes will have different underlying data.

Types of Polymorphism

Compile Time Polymorphism (Static)
Runtime Polymorphism (Dynamic)
● Compile Time Polymorphism : The polymorphism which is implemented at the compile time is known as compile-time polymorphism. Example - Method Overloading

Method Overloading : Method overloading is a technique which allows you to have more than one function with the same function name but with different functionality. Method overloading can be possible on the following basis:

The return type of the overloaded function.
The type of the parameters passed to the function.
The number of parameters passed to the function.
Also, when we made function print in truck,it stopped looking above , it is function overriding.

Base class pointer can point to derived class obj but not vice vis.
And also we can only access props or function using pointer which are also present in base/parent class.

At compile time, we compiler doesnt see the pointer is holding ref of which class, it just sees the class of which the pointer is and calls its method.

Example:
#include <bits/stdc++.h>
using namespace std;
class Base_class{
public:
virtual void show(){
cout << "Apni Kaksha base" << endl;
}
};
class Derived_class : public Base_class {
public:
void show(){
cout << "Apni Kaksha derived" << endl;
}
};
int main(){
Base_class* b;
Derived_class d;
b = &d;
b->show(); // prints the content of show() declared in base class

Runtime Polymorphism : Runtime polymorphism is also known as dynamic polymorphism. Function overriding is an example of runtime polymorphism. Function overriding means when the child class contains the method which is already present in the parent class. Hence, the child class overrides the method of the parent class. In case of function overriding, parent and child classes both contain the same function with a different definition. The call to the function is determined at runtime is known as runtime polymorphism.
Example:
#include <bits/stdc++.h>
using namespace std;
class Base_class{
public:
virtual void show(){ //here
cout << "Apni Kaksha base" << endl;
}
};
class Derived_class : public Base_class {
public:
void show(){
cout << "Apni Kaksha derived" << endl;
}
};
int main(){
Base_class* b;
Derived_class d;
b = &d;
b->show(); // prints the content of show() declared in derived class

Look closely, virtual function is used to enforce run time polymorphism.
If there is no show() in derived class, we call the parent class show(), but if parent class doesnt have a show() it will show error.
Abstract Classes

Pure virtual functions virtual void print()=0; It is just an incomplete function
Any class having pure virtual function is called Abstract class.
It helps in run time polymorphism.
Any class that inherits abstract class has two options:
Either complete all the pure virtual functions and become normal class.
Or become abstract as well.
Also, u cant create an obj of an Abstract class, it throws an error.
It is used when we want run time polymorphism for a function but it cant be defined in the parent class, so we declare it in parent virtually to achieve run time polymorphism and define later in derived class.

Friend Class

Friend Class A friend class can access private and protected members of other class in which it is declared as friend. It is sometimes useful to allow a particular class to access private members of other class. For example, a LinkedList class may be allowed to access private members of Node.

Example:
class Node {
private:
int key;
Node* next;
/* Other members of Node Class */

// Now class  LinkedList can  
// access private members of Node  
friend class LinkedList;   
};

Friend Function
Friend Function Like friend class, a friend function can be given a special grant to access private and protected members. A friend function can be:
a) A member of another class
b) A global function

Example:
class Node {
private:
int key;
Node* next;
/* Other members of Node Class */

// Now class  LinkedList can  
// access private members of Node  
friend int LinkedList::search();
};
Following are some important points about friend functions and classes:

Friends should be used only for limited purpose. too many functions or external classes are declared as friends of a class with protected or private data, it lessens the value of encapsulation of separate classes in object-oriented programming.
Friendship is not mutual. If class A is a friend of B, then B doesn’t become a friend of A automatically.
Friendship is not inherited
The concept of friends is not there in Java.
Access using :: like => A::x=v;
Read about exception handling
