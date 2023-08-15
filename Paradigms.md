## Paradigms

### Object-Oriented Programming (OOP)
Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects," which are instances of classes. Classes act as blueprints or templates for creating objects, and they encapsulate both data (in the form of fields, often referred to as attributes) and behaviors (in the form of methods).
1. Encapsulation
Encapsulation refers to the bundling of data and the methods that operate on that data within a single unit, such as a class. It restricts direct access to some of the object's components, ensuring that certain details are hidden from the outside world and can only be accessed through well-defined interfaces.

2. Inheritance
Inheritance enables a class to inherit properties and methods from one or more existing classes. This allows for code reuse and establishes a relationship between the superclass (or parent class) and the subclass (or child class). The subclass can add or override methods and attributes of the superclass.

3. Polymorphism
Polymorphism allows objects of different types to be treated as objects of a common type. It enables the same method name to be used for different implementations in different classes, which can be invoked dynamically at runtime. This leads to greater flexibility and more maintainable code.

4. Abstraction
Abstraction is the process of hiding the complex reality while exposing only the necessary parts. It helps in reducing complexity by hiding the unnecessary details from the user. Abstraction can be achieved through abstract classes or interfaces.

#### Advantages of OOP
Reusability: Code can be reused through inheritance, allowing for less repetition.
Maintainability: Encapsulation and modularity make it easier to update or modify code without affecting other parts of the program.
Scalability: Object-oriented design provides a clear structure that can be easily expanded.
Security: Encapsulation provides control over access to data, ensuring that it can only be modified in well-defined ways.

#### Prototype
A prototype is essentially an object that serves as a reference for properties and behaviors for other objects. When you create a new object, you can use an existing object as its prototype. The new object will inherit all the properties and methods of the prototype object.

```JavaScript
const animal = {
  makeSound: function() {
    console.log('Some generic animal sound');
  }
};

const dog = Object.create(animal);
dog.makeSound(); // Outputs: Some generic animal sound
```

#### Prototypal Inheritance
Prototypal inheritance is a mechanism in JavaScript (and some other languages) where objects inherit properties and methods from other objects (prototypes). This inheritance chain can be a series of linked objects. If a property or method is not found on an object, the system looks up the chain to the object's prototype, and then to the prototype's prototype, and so on until it finds the property or method or reaches an object with a null prototype.

```JavaScript
const mammal = {
  vertebrate: true,
  breathe: function() {
    console.log('Inhale and exhale');
  }
};

const dog = Object.create(mammal);
dog.bark = function() {
  console.log('Woof!');
};

const myDog = Object.create(dog);
myDog.breathe(); // Outputs: Inhale and exhale
myDog.bark(); // Outputs: Woof!
```

## Functional Programming
Functional programming (FP) is a programming paradigm that treats computation as the evaluation of mathematical functions and avoids changing state or mutable data. It's a declarative paradigm, which means programming is done with expressions or declarations instead of statements. Here are some key concepts and characteristics of functional programming:

#### 1. Pure Functions
Pure functions are a core concept in functional programming. A function is considered pure if it meets two criteria:
    It always produces the same output for the same input.
    It has no side effects, meaning it does not modify any state or variables outside of the function.

#### 2. Immutability
In functional programming, once a variable is set, its value cannot be changed. Instead of modifying existing data structures, new ones are created and the old ones remain unaltered.

#### 3. Higher-Order Functions
Higher-order functions either take one or more functions as arguments or return a function as a result. This feature allows functions to be used just like any other value, enabling powerful abstractions and reusable code.

#### 4. First-Class Functions
Functions are treated as first-class citizens, meaning they can be assigned to variables, passed as arguments, and returned from other functions, just like any other data type.

#### 5. Functional Composition
Functional composition is the process of combining two or more functions to create a new function. It's a way to create complex functions by chaining together simpler ones.

#### 6. Recursion
Functional programming often relies on recursion rather than loops for repetition. A recursive function calls itself with modified arguments until it reaches a base case.

#### 7. Referential Transparency
An expression is said to be referentially transparent if it can be replaced with its corresponding value without changing the program's behavior. This property makes the code more predictable and easier to test and debug.

Here's a simple example using JavaScript, a language that supports functional programming concepts:

```JavaScript
const add = (x, y) => x + y;
const multiply = (x, y) => x * y;
const compose = (f, g) => (x, y) => f(g(x, y));
const addThenMultiply = compose(multiply, add);

const result = addThenMultiply(2, 3); // (2 + 3) * (2 + 3) = 25
```
#### Advantages of Functional Programming

- Predictability: Pure functions and referential transparency make the code more predictable and easier to understand.
- Reusability: Higher-order functions and functional composition enable greater code reusability.
- Testability: Pure functions can be easily tested since they always produce the same output for the same input.

#### Disadvantages

- Performance: The use of immutability can sometimes lead to performance issues, as new objects need to be created instead of modifying existing ones.
- Learning Curve: The concepts and patterns used in functional programming can be unfamiliar to those accustomed to imperative programming paradigms.
- Functional programming is widely used in modern development and supported by languages such as Haskell, Lisp, Erlang, JavaScript (with libraries like Ramda or Lodash), Scala, and others. It offers a robust, expressive, and concise way to write code and can be especially beneficial in applications requiring concurrency or parallel processing.

### Currying

Currying is the process of breaking down a function that takes multiple arguments into a series of functions that each take one argument. It is named after Haskell Curry, a mathematician and logician who contributed to the development of combinatory logic.

Currying allows you to convert a function of the form f(x,y,z) into f(x)(y)(z). Each invocation takes one argument and returns a new function that expects the next argument.

```JavaScript
const multiply = x => y => z => x * y * z;

const multiplyByTwo = multiply(2);
const multiplyByTwoAndThree = multiplyByTwo(3);
const result = multiplyByTwoAndThree(4); // 24
```

#### Why Use Currying?
- Partial Application: Currying allows for the creation of partially applied functions, where some of the arguments are fixed, leading to more reusable and modular code.
- Enhanced Composition: By using currying, you can create more concise and chainable code, making it easier to build complex functions from simpler ones.
- Cleaner Code: Currying promotes a cleaner functional style, making code more readable and maintainable.

### Regex

Regular Expressions are a powerful tool used in programming for searching, manipulating, and editing strings. They provide a concise and flexible means for identifying strings of text that follow a particular pattern or set of rules.

#### Structure
A regular expression is a sequence of characters that forms a search pattern. It can be used for various string operations, such as validation, search, replacement, and splitting. Here's a breakdown of some common components:

- Literals: Regular characters like letters or numbers that match themselves exactly.
- Metacharacters: Special characters that have unique meanings, such as ., *, +, ?, ^, $, and others.
- Character Classes: Represented by square brackets [], they can match any character within the class. For example, [a-z] matches any lowercase letter.
- Quantifiers: Indicate how many instances of a character or group must be present for a match. Examples include * (0 or more), + (1 or more), and {n} (exactly n times).
- Groups and Capturing: Parentheses () are used to group parts of the expression and capture the text matched.

#### Examples
Here are a few examples to illustrate how regex might be used:

- Email Validation: A simple regex pattern to match email addresses might be \w+@\w+\.\w+.
- Finding Dates: A pattern like \d{2}/\d{2}/\d{4} could match dates in the format MM/DD/YYYY.
- Replacing Text: You can use regex with replacement functions to change specific patterns in a string.

- Languages and Tools
Most modern programming languages, including JavaScript, Python, Java, and others, support regex either natively or through libraries. Many text editors and development tools also provide regex-based search and replace functionality.

#### Advantages
- Flexibility: Regex provides a powerful and flexible way to perform complex string manipulations.
- Compactness: Complex patterns and rules can be represented concisely.

#### Disadvantages
- Readability: Complex regex patterns can become difficult to read and maintain.
- Performance: Inefficient regex patterns might lead to performance issues in some scenarios.
