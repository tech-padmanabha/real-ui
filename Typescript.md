# Typescripts basics

## Variables

### Types of variable declaration

```Typescript
let isNew: boolean;
let sum: number;
let firstname: string;
// We can define but less use of this
let work: null;
let property: undefined;
// only we can parse the appropriate value
isNew = false;
sum = 75;
firstname = "Chitralekha";
work = null;
// else we will get compile time error
 firstname = false; // invalid
 property = "SomeName" // invalid
```

> [!NOTE]
> Here in editor we get help type appropriate methods to do
```Typescript
firstname.charAt(2);
firstname.concat("Sahu");
```
### Work with others like array & tuples

```Typescript
let fruits: string[] = ["Orange", "Apple"];
let sumSec: Array<number> = [1, 3, 4, 6];

let person: [string, number] = ["Rajesh", 30];
```

### Work with enum

```Typescript
enum Colors {
  Red,
  Green,
  Black = 240,
  White,
  Yellow,
}

let w: Colors = Colors.White;
console.log(w);
```

> [!NOTE]
> Here at enum initial index starts from zero or we can provide custom values as well, After that goes increment order

### Work with any and unknown

```Typescript

let myVariable: any = 10; // as number
myVariable = "Rajesh Gupta"; // as string
myVariable = false; // as boolean
 console.log(myVariable.name); // as object
 myVariable(); // as function
 myVariable.toUpperCase(); // can use method asuming as string

```

> [!NOTE]
> Here we won't get any compile time error but in runtime acxures to resolve this issue folow below

```Typescript
let yourVariable: unknown = "Sahid";

console.log(yourVariable.name); // invalid
yourVariable(); // invalid
(yourVariable as string).toUpperCase(); // valid
console.log(yourVariable);
```

### Union types and default type

```Typescript
let x;
x = false;
x = "Some String";
x = 8001;
//  It doesn't show any error because x by default takes as 'any' type to restrict falow below steps 
let y = 10;
 y = false; // invalid
 y = "Suresh "; // invalid
```

> [!NOTE]
> Here If we provide the initial value TS understand the value and provide the intelisence

```TS
let multiType: number | boolean;

multiType = 10;
multiType = false;

```
### Functions
> Normal Function
```Typescript
export {};

function add(num1: number, num2: string) {
  return num1 + num2;
}
 //Here we can specify the return type
function sub(num1: number, num2: number): number {
  return num1 - num2;
}
const sum = add(10, "Hari");
```

> Optional Function

```Typescript

function mul(num1: number, num2?: number): number {
  if (num2) {
    return num1 * num2;
  } else {
    return num1;
  }
}

mul(10, 20);
mul(10);
```

 > [!NOTE]
 > Optional params we can define n number of params

 > [!IMPORTANT]
 > Optional params is always after the required params

> Default Value Function

```Typescript

function calc(num1: number, num2: number = 5): number {
  if (num2) {
    return num1 * num2;
  } else {
    return num1;
  }
}

let value = calc(10, 20);
let value2 = calc(10);
console.log(value2);
```
### Interface
> Represent Object
```Typescript
export {};

 function getPerson(person: { firstName: string; lastName: string }) {
   console.log(`${person.firstName} ${person.lastName}`);
 }
 let p = {
   firstName: "Harish",
   lastName: "Jain",
   address: "Bang",
   dob: "12-Mar-2000",
 };
 let details = getPerson(p);

```

 > [!CAUTION]
 > Here we will not get any error. Address and dob are uselesee to pass

> By Using Interface we can restrict

```Typescript

interface Person {
  firstName: string;
  lastName?: string;
}

function getPerson(person: Person) {
  console.log(`${person.firstName} ${person.lastName}`);
}
let p = {
  firstName: "Harish",
  lastName: "Jain",
  address: "Bang",
  dob: "12-Mar-2000",
};
let details = getPerson(p);
```

### Class & modifier
> Represent Object
```Typescript
class Parent {
  protected firstname: string;
  protected lastname: string;

  constructor(fName: string, lName: string) {
    this.firstname = fName;
    this.lastname = lName;
  }

  getLastName() {
    console.log(this.lastname + " is you identity");
  }
}

class Child extends Parent {
  constructor(fName: string, lName: string) {
    super(fName, lName);
  }

  greet() {
    console.log(this.lastname);
  }
}

let person = new Parent("Padmanabha", "Sahu");
person.getLastName();
console.log(person.firstname, person.lastname);

let child = new Child("Chitralekhs", "Sahu");
child.getLastName();
console.log(child.firstname, child.lastname);
```
 > [!CAUTION]
 > Here we will get error firstname or lastname we can't access outside parent clild releationship. Here if we change the modifier to private then clild classes can not access as well. By default is public.

