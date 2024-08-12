+++
comments = true
date = "2015-03-16T15:36:49+01:00"
image = ""
tags = ["golang", "inheritance", "java"]
title = "Go and Inheritance"
toc =  false
readTime = true
autonumber = false
+++

Inheritance is an essential feature in many programming languages and trying to imagine the absence of it will bring up many thoughts, including code repetition.

It is interesting that the few times I have had a discussion with someone not comfortable with the lack of inheritance in Go, code repetition has been their issue. The issue is not the lack of inheritance, the issue is they are used to having inheritance. it is best to think the Go way to code in Go.

Java is one of the strongest cases for inheritance and yet James Gosling who is widely regarded as the father of Java, said this about inheritance. You can read full transcript [here](http://www.artima.com/intv/gosling3P.html).

> _"Yes -- without an inheritance hierarchy. Rather than subclassing, just use pure interfaces. It's not so much that class inheritance is particularly bad. It just has problems."_

With that, you would reason with the Go creators for the choice to leave out inheritance. However, and they did not leave out inheritance without providing a way around it. In this post, I will provide a direct comparison between Java and Go. Showing how the features that inheritance brings to Java is still implemented in Go without it.

### Subtyping

Typical scenario in Java is to have a class `Person` and you want a class `Student` that is derived from Person. Let us see how this is done in Java.

```java
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

In the example above, the class `Student` is extending `Person` and overriding the `print()` method. If required, Java provides a way to access an overridden method of the base class using `super.print()`. Now let us see how we can do the same in Go without inheritance.
```go
type Person struct {
  Name  string
  Age   int
}

func (p *Person) Print()
  fmt.Printf("%s is %d years old", p.Name, p.Age){
}

type Student struct {
  Person
  StudentId   string
  YearOfStudy int
}

func (s *Student) Print(){
  fmt.Printf("%s is a student with Student Id: %s", s.Name, s.StudentId)
}
```

In the example above, you see the use of [Type Embedding](https://golang.org/doc/effective_go.html#embedding) in Go. Go provides the ability to embed one type into another and through type promotion, have the identifiers of the inner type be accessible by values of the outer type. As you can see when we called `s.Name`, `Name` was declared by `Person` type but we are able to access that field  from a value of `Student` type.

You may be wondering how you can access the inner type directly? We can still explicitly call `Print()` from the inner type by using the name of the inner type. `student.Person.Print()`.

```go
student := Student{
  Person{"John", 20},
  "72636",
  "2",
}
student.Print()         //Outputs John is a student with Student Id: 72636
student.Person.Print()  //Outputs John is 20 years old
```

### Interfaces
Gophers claim this is one of the sweetest part of Go and I have no exception. Interfaces in Go are painless compared to Java. Let us look at the following Java code.

```java
interface StringReader {
  public int read(byte[] b);
}

interface BytesReader{
  public int read(byte[] b);
}

class FileReader implements StringReader {
  public int read(byte[] b){ ... }
}
```

In Java, you must use the `implements` keyword to specify the interface is being implemented. `FileReader` is not valid when the `BytesReader` interface is required, even though it has the required method.

This is one thing Go has done right.

```go
type StringReader interface {
  Read(b []byte) (int, error)
}

type BytesReader interface {
  Read(b []byte) (int, error)
}

type FileReader struct { ... }

func (f *FileReader) Read(b []byte) (int, error) { ... }
```

With Go, as long as the method declared by the interface has been implemented, values from these types are said to implement the interface. Pointers of type `FileReader` implements both the `StringReader` and `ByteReader` interfaces. You do not need to use any keywords to define the relationship, it  is just implemented.

So where is the feared code repetition?

Inheritance may be missing in Go but Go is not missing the features that inheritance brings to Java.
