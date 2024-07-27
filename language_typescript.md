# [TypeScript](https://www.typescriptlang.org/)

TypeScript is a superset of JavaScript that adds static typing to the language.

## Table of Contents

- [TypeScript](#typescript)
  - [Table of Contents](#table-of-contents)
  - [Primitive Types](#primitive-types)
    - [Strings, String Literal](#strings-string-literal)
    - [Numbers, Numeric Literals](#numbers-numeric-literals)
    - [Boolean](#boolean)
    - [Any Type](#any-type)
    - [Null Type](#null-type)
    - [Undefined Type](#undefined-type)
    - [Unknown Type](#unknown-type)
    - [Union Type](#union-type)
  - [Object Types](#object-types)
    - [Arrays](#arrays)
    - [Functions](#functions)
    - [Anonymous Objects](#anonymous-objects)
    - [Type Alias](#type-alias)
    - [Interfaces](#interfaces)
    - [Enums](#enums)
      - [Numeric Enums](#numeric-enums)
      - [String Enums](#string-enums)
      - [Union Enums and Enum Member Types](#union-enums-and-enum-member-types)
      - [Enums at Compile Time](#enums-at-compile-time)
      - [Enum Reverse Mappings](#enum-reverse-mappings)
      - [Constant Enums (Single Instance)](#constant-enums-single-instance)
  - [Type Assertions](#type-assertions)
  - [Type Narrowing](#type-narrowing)
    - [Type Guard Narrowing](#type-guard-narrowing)
    - [Truthiness Narrowing](#truthiness-narrowing)
      - [Coerced -\> false](#coerced---false)
      - [All Others Coerce -\> true](#all-others-coerce---true)

---

## Primitive Types

### Strings, String Literal

```typescript
const x: string = 'hello';
```

### Numbers, Numeric Literals

```typescript
const x: number = 42.0;
```

### Boolean

```typescript
const x: boolean = true;
```

### Any Type

```typescript
const x: any = ...
```

### Null Type

```typescript
const x: null = null;
```

### Undefined Type

```typescript
const x: undefined = undefined;
```

### Unknown Type

```typescript
const x: unknown = ...
```

### Union Type

```typescript
const id: number | string = ...
```

## Object Types

### Arrays

```typescript
let my_array: string[] = ['hello', 'world'];
```

```typescript
let an_array: number[] = [1, 2, 3, ...];
```

### Functions

```typescript
function myTypedFunction(
 x: string = "Hello",
 y: number[] = [1,2,3]
): string[] {
 ...
 return ['list', 'of', 'strings']
}
```

### Anonymous Objects

```typescript
let obj_literal = {
 x: string,
 y: number,
 o?: boolean
};
```

Here is an example of an anonymous object applied to a function parameter:

```typescript
function greet(person: { name: string; age: number }): string {
  if (age < 21) {
    return 'You must be 21 years old';
  }
  return 'Hello ' + person.name;
}
```

### Type Alias

Type aliases are **immutable** constructs.

```typescript
type ID = number | string;
```

```typescript
type Point = {
  x: number;
  y: number;
};
```

Here is an example of a type alias applied to a function parameter:

```typescript
type Person = {
  name: string;
  age: number;
};

function greet(person: Person) {
  return 'Hello ' + person.name;
}
```

### Interfaces

Interfaces are similar to a type alias but vary mainly in that types are immutable, whereas interfaces are extendable.

```typescript
interface Point {
  x: number;
  y: number;
}

interface Line extends Point {
  d: number;
}
```

Interfaces may also be applied in the same way that type aliases are applied. There are some nuances.

```typescript
interface Person {
  name: string;
  age: number;
}

function greet(person: Person) {
  return 'Hello ' + person.name;
}
```

### Enums

- define a set of named constants
- can make it easier to document intent
- create a set of distinct cases

#### Numeric Enums

```typescript
// initialized
enum Direction {
  Up = 1, // 1
  Down, // 2
  Left, // 3
  Right, // 4
}

// un-initialized
enum Direction {
  Up, // 0
  Down, // 1
  Left, // 3
  Right, // 4
}
// applied use case
enum Vote {
  No = 0,
  Yes = 1,
}
```

Here is an example of Enums applied to the parameters of a function:

```typescript
function countBallot(
 candidate: string,
 counted: Vote
): void {
 ...
}
countBallot( "Joseph Grable", Vote.Yes );
```

#### String Enums

```typescript
enum Direction {
  Up = 'UP',
  Down = 'DOWN',
  Left = 'LEFT',
  Right = 'RIGHT',
}
```

#### Union Enums and Enum Member Types

```typescript
enum ShapeKind {
  Circle,
  Square,
}

interface Circle {
  kind: ShapeKind.Circle;
  radius: number;
}

interface Square {
  kind: ShapeKind.Square;
  sideLength: number;
}
```

#### Enums at Compile Time

```typescript
enum LogLevel {
  ERROR,
  WARN,
  INFO,
  DEBUG,
}

// This is equivalent to:
type LogLevelStrings = 'ERROR' | 'WARN' | 'INFO' | 'DEBUG';
type LogLevelStrings = keyof typeof LogLevel;
```

#### Enum Reverse Mappings

```typescript
enum Enum {
 A,
}
let a = Enum.A;
let nameOfA = Enum[a];      # "A"
```

#### Constant Enums (Single Instance)

```typescript
const enum Enum {
  A = 1,
  B,
}
```

## Type Assertions

```typescript
const p1 = addCanvasPoint(5, 10) as Point;

const p2 = addCanvasPoint<Point>(10, 5);

const ln1 = getCanvasLine(p1, p2) as Line;

const ln2 = getCanvasLine<Line>(p1, p2);
```

## Type Narrowing

### Type Guard Narrowing

Use `typeof` to identify and act on variables or values of a certain type.

```typescript
if ( typeof x === "boolean" ) {
 ... do something if x is bool
}

if ( typeof x === "string" ) {
 ... do something if x is string
}
```

Type guard narrowing may be applied to the following types

- string
- number
- bigint
- boolean
- symbol
- undefined
- object
- function

### Truthiness Narrowing

#### Coerced -> false

```typescript
0
NaN
""          # the empty string
0n          # the bigint version of zero
null
undefined
```

#### All Others Coerce -> true

```typescript
1
"Hello"
\[2, 3]
{ "hello": "world" }
```
