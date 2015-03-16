+++
comments = true
date = "2015-03-16T15:36:49+01:00"
image = ""
slug = "go-and-inheritance"
tags = ["golang", "inheritance", "java"]
title = "Go and Inheritance"
+++
Inheritance is an essential feature in programming languages and trying to imagine the absence of it will bring up many thoughts, including code repetition.

It is interesting that the few times I have had a discussion with someone not comfortable with lack of inheritance in Go, code repetition has been their topic. The issue is not lack of inheritance, the issue is being used to inheritance. You have to think the Go way to code in Go.

Java is one of the strongest cases for inheritance and yet James Gosling who is widely regarded as the father of Java, said this about inheritance. You can read full transcript [here](http://www.artima.com/intv/gosling3P.html). 

> _"Yes -- without an inheritance hierarchy. Rather than subclassing, just use pure interfaces. It's not so much that class inheritance is particularly bad. It just has problems."_

With that, you would reason with Go creators for the choice to leave out inheritance and they do not leave out inheritance without providing a way out. I would do a direct comparison with Java and how you can do it in Go without (normal) inheritance.

### Subtyping
Typical scenario is you have a class Person and you want a class Student that is based on Person. Let us see how it is done in Java.

```
class Person {
  String name;
  int age;

  public void print(){
    System.out.printf("%s is %d years old", name, age);
  }
}

class Student extends Person {
  String studentId;
  int yearOfStudy
    
  public void print(){
    System.out.printf("%s is a student with Student Id: %s", name, studentId)
  }
}
```
Class `Student` was able to extend `Person` and override the `print()` method. If required, Java provides a way to an overriden method of the parent using `super.print()`. Now let us see how we would do this in Go.
```
type Person struct {
  Name  string
  Age   int  
}

func (p *Person) Print()
  fmt.Printf("%s is %d years old", p.Name, p.Age){
}

type Student struct {
  *Person
  StudentId   string
  YearOfStudy int
}

func (s *Student) Print(){
  fmt.Printf("%s is a student with Student Id: %s", s.Name, s.StudentId)
}
```
What we did there is [Type Embedding](https://golang.org/doc/effective_go.html#embedding). Go provides the ability to embed one type into another and mirror the properties of the embedded type into the parent type. As you can see when we called `s.Name`, `Name` belongs to `Person` but we are able to call it inside `Student` as if it is a member of `Student`.

You may be wondering how you will access the parent type, like you would do with `super` in Java. We can still explicitly call `Print()` of the parent type by using the variable that is named the embedded type. `student.Person.Print()`.
```
student := Student{
  &Person{"John", 20},
  "72636",
  "2",
}
student.Print()         //outputs John is a student with Student Id: 72636
student.Person.Print()  //outputs John is 20 years old
```
### Interfaces
Gophers claim this is one of the sweetest part of Go and I am no exception. Interfaces in Go are painless compared to Java. Let us look at the following Java code.
```
interface Reader {
  public int read(byte[] b);
}

interface Reader2{
  public int read(byte[] b);
}

class FileReader implements Reader {
  public int read(byte[] b){ ... }
}
```
In Java, you must use the `implements` keyword to specify the interface being implemented. `FileReader` is not valid when `Reader2` interface is required, even though it has the required method. 

This is one thing Go has done right.
```
type Reader interface {
  Read(b []byte) (int, error)
}

type Reader2 interface {
  Read(b []byte) (int, error)
}

type FileReader struct { ... }

func (f *FileReader) Read(b []byte) (int, error) { ... }
```
With Go, as long as the function is present, it is valid anywhere the interface is required. `FileReader` is valid for both `Reader` and `Reader2` interfaces and you do not need to use any keywords to define the relationship, it just works.

So where is the feared code repetition? 

Inheritance may be missing in Go but Go is not missing inheritance.
