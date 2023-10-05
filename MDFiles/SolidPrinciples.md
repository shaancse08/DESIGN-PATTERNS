## Solid Principles

Defined long ago, the `SOLID` principles are intended to improve the readability, adaptability, extensibility, and maintainability of object-oriented designs. The five `SOLID` principles of object-oriented class design facilitate the development of understandable, tested software that many developers can use at any time and place.

We give Robert C. Martin, popularly known as Uncle Bob, credit for this idea in his 2000 work, Design Principles and Design Patterns. He’s also known for the best-selling books Clean Code and Clean Architecture. The abbreviation `SOLID` was later coined by Michael Feathers to illustrate the ideas identified by Uncle Bob.

In this article, we’ll go over each of the `SOLID` principles, providing TypeScript examples to illustrate and understand them. Let’s get started!

## S: Single-responsibility principle:

According to the single-responsibility principle, a class should be responsible for only one activity and only have one cause to change. This rule also includes modules and functions.

Let’s consider the example below:

```javascript
class Student {
  public createStudentAccount(){
    // some logic
  }

  public calculateStudentGrade(){
    // some logic
  }

  public generateStudentData(){
    // some logic
  }
}
```

The idea of a single duty is broken in the `Student` class above. As a result, we should divide the `Student` class into different states of responsibility. According to SOLID, the idea of responsibility is a reason to change.

To pinpoint a reason to change, we need to look into what our program’s responsibilities are. We might change the `Student` class for three different reasons:

- The createStudentAccount computation logic changes
- The logic for calculating `student` grades changes
- The format of generating and reporting student data changes

The single-responsibility principle highlights that the three aspects above put three different responsibilities on the Student class:

```javascript
class StudentAccount {
  public createStudentAccount(){
    // some logic
  }
}


class StudentGrade {
  public calculateStudentGrade(){
    // some logic
  }
}


class StudentData {
  public generateStudentData(){
    // some logic
  }
}
```

Now that we‘ve divided the classes, each has only one duty, one responsibility, and only one alteration that needs to be made. Now, our code is simpler to explain and comprehend.
