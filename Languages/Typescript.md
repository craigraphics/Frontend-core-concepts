## Typescript
TypeScript is a superset of JavaScript that adds static types. It was developed and maintained by Microsoft, and it was first released in 2012. Here's a more detailed overview:

### Main Features
1. **Static Type Checking**: TypeScript adds strict syntactical and semantic checks to your code. This provides an additional layer of security to catch errors during development rather than at runtime.

2. **Type Annotations**: You can declare the type of a variable, function parameters, return type, etc., giving you more control over your code and ensuring type safety.

3. **Type Inference**: Even if you don't explicitly type variables, TypeScript can infer the type based on how the code operates on those variables.

4. **Interfaces**: Interfaces in TypeScript enable you to define complex types and ensure conformity to specific structures. This enhances code quality and understandability.

5. **Generics**: Generics enable you to write reusable and type-safe functions and classes without committing to a specific type.

6. **Support for Modern JavaScript Features**: TypeScript includes support for features from ECMAScript standards that might not be supported in all browsers.

7. **Tooling and Integration**: Most modern IDEs support TypeScript, providing advanced autocompletion, refactoring, and navigation features that can lead to more robust development experiences.

### Compilation
TypeScript code must be transcompiled into JavaScript, as browsers do not understand TypeScript natively. The TypeScript compiler, `tsc`, takes TypeScript files and compiles them into standard JavaScript, allowing them to run in a browser or a server environment using Node.js.

### Benefits
- **Code Quality**: With static typing and better tooling, it's easier to maintain and refactor code, thus reducing the possibility of bugs.
- **Collaboration**: Type annotations make it easier for developers to understand code, leading to more efficient collaboration in a team environment.
- **Scalability**: TypeScript's features make it suitable for large-scale applications where maintaining code quality is essential.

### Drawbacks
- **Learning Curve**: For developers new to typed languages, TypeScript may add complexity.
- **Compilation Step**: The need to compile TypeScript into JavaScript can be seen as an additional step in the development process.

***
## Types
In TypeScript, types are a powerful way to describe the shape and behavior of an object within the code. They provide a way to specify what kind of values are permitted for a particular variable, parameter, or return value. Here's an overview of the primary types in TypeScript:

1. **Primitive Types**:
   - **Number**: Represents both floating-point and integer values.
   - **String**: Represents a sequence of characters.
   - **Boolean**: Represents a true or false value.
   - **Symbol**: Represents a unique value that's not equal to any other value.
   - **Undefined**: A variable that hasn't been assigned a value.
   - **Null**: Represents an intentional absence of an object value.

2. **Object Types**:
   - **Array**: Defines a type for arrays of specific types. For example, `number[]` or `Array<number>`.
   - **Tuple**: Like an array, but you can define the type of each element at specific positions.
   - **Interface**: Allows you to describe the shape of an object, with optional properties and methods.
   - **Class**: Classes also define types, especially when used with the `new` operator.

3. **Union Types**: Allows a value to be one of several types. For example, `string | number` allows a value to be either a string or a number.

4. **Intersection Types**: Combines multiple types into one, requiring a value to meet all of the combined types. For example, `A & B` means a value must meet both type A and type B.

5. **Literal Types**: Allows a variable to be exactly one specific value. For example, `'hello'` as a type means the variable must be exactly the string 'hello'.

6. **Enum**: A way to define a set of named constants, either numeric or string values.

7. **Generics**: Allows the creation of reusable components that can work over various types rather than a single one.

8. **Any**: A type that can represent any value. It bypasses type-checking, so it's best to use it sparingly.

9. **Unknown**: Similar to `any`, but more type-safe, as you must perform some type of checking before performing operations on a value of type `unknown`.

10. **Void**: Often used as the return type for functions that don't return a value.

11. **Never**: Represents a value that never occurs. For example, a function that throws an exception and never returns a value.

12. **Type Aliases**: You can define a new name for a type using the `type` keyword, allowing for more flexible and readable code.

13. **Mapped Types**: Allows you to create new types based on existing ones, transforming properties as needed.

14. **Conditional Types**: Types that select one of two possible types based on a condition.

15. **Utility Types**: TypeScript provides various utility types like `Partial`, `Readonly`, `Pick`, and `Omit` to manipulate types in various ways.


***
## Generics

Generics in TypeScript provide a way to create reusable components that can work over a variety of types rather than a single one. This allows you to write more maintainable and scalable code without losing type safety.

### Introduction to Generics

Imagine you are writing a function that takes an array and returns its first element. Without generics, you might write separate functions for arrays of numbers, strings, objects, etc. With generics, you can write a single function that works with arrays of any type.

### Basic Syntax

Here's a basic example of a generic function:

```typescript
function firstElement<T>(arr: T[]): T {
  return arr[0];
}
```

Here, `T` is a type variable, a stand-in for any type. You can call this function with an array of numbers, strings, or any other type, and TypeScript will ensure that the correct type is returned:

```typescript
let numbers = firstElement([10, 20, 30]); // Type is number
let strings = firstElement(["a", "b", "c"]); // Type is string
```

### Generic Constraints

Sometimes, you might want to work with a part of a type, such as a specific method that exists on various classes. You can use constraints to limit the types that are acceptable.

```typescript
interface HasLength {
  length: number;
}

function lengthOf<T extends HasLength>(obj: T): number {
  return obj.length;
}
```

This function now works with any value that has a `length` property of type `number`.

### Generic Classes

Generics can also be used with classes:

```typescript
class Box<T> {
  private content: T;

  constructor(content: T) {
    this.content = content;
  }

  getContent(): T {
    return this.content;
  }
}

let numberBox = new Box(42); // Box<number>
let stringBox = new Box("hello"); // Box<string>
```

### Generic Utility Types

TypeScript also includes several built-in generic utility types, like `Partial`, `Readonly`, `Record`, etc., that you can use to transform types in various ways.

***
### Union Types

Union Types in TypeScript allow a value to be one of several types. This is useful when a variable can legitimately have more than one type, and it enables you to model such scenarios in a type-safe way. Union types are expressed using the `|` symbol between the types that the variable can be.

### Basic Syntax

Here's a basic example of a union type:

```typescript
let value: string | number;
value = 'hello'; // Valid
value = 42;      // Valid
value = true;    // Error
```

The variable `value` can be either a string or a number, but no other types are allowed.

### Using Union Types in Functions

You can use union types in function parameters and return values to make functions more flexible:

```typescript
function formatInput(input: string | number): string {
  return String(input);
}
```

### Narrowing

When you're working with a variable of a union type, TypeScript needs to know which specific type the variable is at any given point. This process is known as narrowing. You can narrow the type using type guards such as `typeof`, `instanceof`, or custom functions:

```typescript
function printLength(input: string | number[]) {
  if (typeof input === 'string') {
    console.log(input.length); // Input is a string here
  } else {
    console.log(input.length); // Input is a number[] here
  }
}
```

### Discriminated Unions

Discriminated unions, also known as tagged unions or algebraic data types, provide a way to handle complex types with a common property that you can use to tell the types apart:

```typescript
type Shape = 
  { kind: 'circle'; radius: number } |
  { kind: 'square'; sideLength: number };

function area(shape: Shape): number {
  switch (shape.kind) {
    case 'circle':
      return Math.PI * shape.radius ** 2;
    case 'square':
      return shape.sideLength ** 2;
  }
}
```

Here, the `kind` property is used to determine which specific type the `shape` variable is.

### Conclusion

Union types in TypeScript provide a powerful way to model scenarios where a value can be one of several types. This leads to more flexible and maintainable code, with TypeScript's type checking ensuring that you're handling all possible types correctly. Whether you're dealing with basic unions of primitive types or complex discriminated unions, this feature enables you to write expressive, type-safe code.


***
## Intersection Types

Intersection Types in TypeScript allow you to combine multiple types into one. This enables you to mix several structures together to create a new one, meaning that a variable with an intersection type must meet all the combined types. Intersection types are denoted by the `&` symbol.

### Basic Syntax

Here's an example of an intersection type:

```typescript
type First = { a: number; b: string };
type Second = { b: number; c: boolean };

type Intersection = First & Second;

// An object of type Intersection must contain all properties from First and Second
let value: Intersection = { a: 1, b: 2, c: true };
```

### Combining Different Types

You can combine any types, not just object types, including primitives, unions, interfaces, and more.

```typescript
interface Named {
  name: string;
}

class Person {
  constructor(public name: string) {}
}

type LoggingLevel = 'debug' | 'info' | 'warn';

type Developer = Named & { loggingLevel: LoggingLevel };

const developer: Developer = {
  name: 'Alice',
  loggingLevel: 'info',
};
```

### Using Intersection Types in Functions

Intersection types can be used in function parameters to create more flexible interfaces:

```typescript
function printDetails(details: Named & { age: number }) {
  console.log(`Name: ${details.name}, Age: ${details.age}`);
}
```

### Mixing Intersection Types with Generics

You can combine intersection types with generics to create highly reusable code structures:

```typescript
function extend<T, U>(first: T, second: U): T & U {
  const result = {} as T & U;
  for (const id in first) {
    (result as any)[id] = (first as any)[id];
  }
  for (const id in second) {
    if (!result.hasOwnProperty(id)) {
      (result as any)[id] = (second as any)[id];
    }
  }
  return result;
}
```

This `extend` function takes two objects and returns a new object that combines both of them.

### Caveats and Considerations

While intersection types are powerful, they might lead to confusion if not used judiciously. Specifically, if you combine two types that have properties with the same name but different types, it can lead to a type that might be impossible to instantiate, as in the first example.



***
## Utility Types

Utility Types provide a set of type transformations that you can use to manipulate types in various ways. They are like functions but operate on types, allowing you to create new types based on existing ones. These transformations can make your code more expressive and maintainable. Here's a brief overview of some of the most common utility types:

### 1. `Partial<Type>`
This creates a type with all the properties of `Type` set to optional. It's useful when you want to represent a subset of a given type.

```typescript
type MyType = { a: number; b: string };
type PartialMyType = Partial<MyType>; // { a?: number; b?: string }
```

### 2. `Readonly<Type>`
This creates a type where all properties of `Type` are read-only.

```typescript
type ReadOnlyMyType = Readonly<MyType>; // { readonly a: number; readonly b: string }
```

### 3. `Pick<Type, Keys>`
Allows you to create a new type by picking specific properties from a given type.

```typescript
type PickedType = Pick<MyType, 'a'>; // { a: number }
```

### 4. `Omit<Type, Keys>`
Allows you to create a new type by omitting specific properties from a given type.

```typescript
type OmittedType = Omit<MyType, 'a'>; // { b: string }
```

### 5. `Record<Keys, Type>`
Allows you to create an object type with specified keys and the same value type.

```typescript
type NumberRecord = Record<'one' | 'two', number>; // { one: number; two: number }
```

### 6. `Extract<Type, Union>`
Extracts from `Type` those types that are assignable to `Union`.

```typescript
type T0 = Extract<"a" | "b" | "c", "a" | "f">;  // "a"
```

### 7. `Exclude<Type, Union>`
Excludes from `Type` those types that are assignable to `Union`.

```typescript
type T1 = Exclude<"a" | "b" | "c", "a" | "f">;  // "b" | "c"
```

### 8. `NonNullable<Type>`
Excludes `null` and `undefined` from `Type`.

```typescript
type T2 = NonNullable<"a" | null | undefined>;  // "a"
```

### 9. `ReturnType<Type>`
Constructs a type consisting of the return type of a function `Type`.

```typescript
type T3 = ReturnType<() => string>;  // string
```


***
## Namespaces

Namespaces in TypeScript are a way to organize code and encapsulate functionalities. They provide a container for grouping variables, functions, interfaces, classes, and even other namespaces, allowing you to avoid naming collisions and create a modular structure.

Namespaces can be seen as a way to logically group related code and provide a level of scoping, making it easier to maintain and understand the codebase.

### Declaration

You can declare a namespace using the `namespace` keyword. Here's an example:

```typescript
namespace MyNamespace {
  export class MyClass {
    constructor(public message: string) {}
  }

  export function MyFunction() {
    return 'Hello World';
  }
}
```

### Exporting and Importing

Within a namespace, you can use the `export` keyword to make properties accessible outside the namespace. Without exporting, they remain private to the namespace.

To access an exported element from outside the namespace, you need to use the namespace name as a prefix:

```typescript
let instance = new MyNamespace.MyClass('Hello');
console.log(MyNamespace.MyFunction()); // Outputs: 'Hello World'
```

### Nested Namespaces

Namespaces can be nested inside other namespaces, allowing for a hierarchical organization:

```typescript
namespace ParentNamespace {
  export namespace ChildNamespace {
    export function MyFunction() {
      return 'Nested Namespace';
    }
  }
}

console.log(ParentNamespace.ChildNamespace.MyFunction()); // Outputs: 'Nested Namespace'
```

### Merging

In TypeScript, you can declare multiple namespaces with the same name in different locations, and they will be merged together:

```typescript
namespace MyNamespace {
  export function FunctionA() {
    return 'Function A';
  }
}

namespace MyNamespace {
  export function FunctionB() {
    return 'Function B';
  }
}

console.log(MyNamespace.FunctionA()); // Outputs: 'Function A'
console.log(MyNamespace.FunctionB()); // Outputs: 'Function B'
```

### Usage with Modules

With the modern ES6 module system, the need for namespaces has been largely reduced, as modules themselves provide a way to organize and encapsulate code. However, namespaces are still useful in certain scenarios, especially in larger codebases or when you need to merge declarations.


***
## Interfaces
In TypeScript, interfaces are a powerful way to define contracts within your code. They are used to define the shape of an object, ensuring that the object has certain properties with specific types.

### Definition and Usage

An interface in TypeScript is used to define a type that represents a contract for classes to implement or for objects to adhere to. It can include properties, methods, and index signatures.

### Examples

Here's an example of an interface that describes a basic structure for a `Person` object:

```typescript
interface Person {
  firstName: string;
  lastName: string;
  age?: number; // Optional property
  greet(): void; // Method signature
}

const john: Person = {
  firstName: 'John',
  lastName: 'Doe',
  greet() {
    console.log(`Hello, my name is ${this.firstName} ${this.lastName}`);
  },
};
```

### Interfaces and Classes

Interfaces can be used with classes to ensure that the class adheres to a particular contract. Any class that implements an interface must provide an implementation for all the properties and methods defined by that interface.

```typescript
interface Animal {
  name: string;
  makeSound(): void;
}

class Dog implements Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  makeSound() {
    console.log('Woof!');
  }
}
```

### Extending Interfaces

Interfaces can extend one or more other interfaces, inheriting all their properties and methods.

```typescript
interface Shape {
  area(): number;
}

interface Circle extends Shape {
  radius: number;
}

const circle: Circle = {
  radius: 5,
  area() {
    return Math.PI * this.radius ** 2;
  },
};
```

### Advantages of Interfaces

1. **Code Consistency:** They help enforce consistent structures across your codebase, reducing errors.
2. **Code Reusability:** You can define common structures or behaviors across multiple parts or classes of your application.
3. **Enhanced Tooling:** Many code editors provide better support and autocompletion for code that uses interfaces.


***
## Enums
Enums (short for enumerations) are a feature that allows you to define a set of named constants. They can make your code more readable and expressive by allowing you to use descriptive names for values.

### Numeric Enums

By default, enums are numeric, and they are zero-based. Here's an example:

```typescript
enum Direction {
  North,
  East,
  South,
  West,
}

let currentDirection: Direction = Direction.North;
```

In this example, `Direction.North` has a value of `0`, `Direction.East` has a value of `1`, and so on.

You can also manually set the values:

```typescript
enum Direction {
  North = 1,
  East = 2,
  South = 3,
  West = 4,
}
```

### String Enums

TypeScript also allows you to define string enums, where the values are initialized with string literals:

```typescript
enum Direction {
  North = 'NORTH',
  East = 'EAST',
  South = 'SOUTH',
  West = 'WEST',
}
```

### Const Enums

If you want to ensure that the enum values are inlined during compilation, you can define a const enum:

```typescript
const enum Direction {
  North,
  East,
  South,
  West,
}
```

Const enums are removed during compilation, and only the values are left in the resulting JavaScript.

### Computed Enums

You can also use computed values in an enum:

```typescript
enum FileAccess {
  None,
  Read = 1 << 1,
  Write = 1 << 2,
  ReadWrite = Read | Write,
}
```

### Using Enums

You can use enums just like any other type in TypeScript:

```typescript
function printDirection(direction: Direction) {
  console.log(direction);
}

printDirection(Direction.North); // Outputs: 'NORTH' if using string enum or '0' if using numeric enum
```

***
## Decorators
Decorators are a stage 2 proposal for JavaScript and an experimental feature in TypeScript. They provide a way to add annotations and modify classes, properties, methods, or parameters using higher-order functions.

Decorators allow developers to write cleaner code by separating concerns and adding functionalities to objects in a declarative way.

### Types of Decorators

1. **Class Decorators**: Applied to the constructor of the class.
2. **Property Decorators**: Applied to the properties of classes.
3. **Method Decorators**: Applied to the methods of classes.
4. **Accessor Decorators**: Applied to the get and/or set accessors.
5. **Parameter Decorators**: Applied to parameters of class constructors or methods.

### How to Use Decorators

Here's a basic example of a class decorator:

```typescript
function logClass(target: Function) {
  console.log(`Class created: ${target}`);
}

@logClass
class MyClass {
  // ...
}
```

This `@logClass` decorator will log the class when it's defined.

### Example of a Method Decorator

Here's how you might create a method decorator that logs whenever the method is called:

```typescript
function logMethod(target: Object, propertyKey: string, descriptor: TypedPropertyDescriptor<any>) {
  const originalMethod = descriptor.value;

  descriptor.value = function (...args: any[]) {
    console.log(`Method ${propertyKey} called with args: ${JSON.stringify(args)}`);
    return originalMethod.apply(this, args);
  };

  return descriptor;
}

class MyClass {
  @logMethod
  myMethod(arg1: string, arg2: number) {
    // ...
  }
}
```

This `@logMethod` decorator will log any calls to `myMethod` along with the arguments passed.

### Enabling Decorators

Since decorators are considered experimental, you'll need to enable them in your `tsconfig.json` file:

```json
{
  "compilerOptions": {
    "experimentalDecorators": true
  }
}
```
