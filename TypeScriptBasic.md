### Javascript의 변수 애매모호성을 없애기 위함

```tsx
let helloWorld = "Hello World";

let helloWorld: string;
```

<br>

### Typescript로 object 지정하기

```tsx
interface User {
  name: string;
  id: number;
}
const user: User = {
  name: "Hayes",
  id: 0,
};
```

- 클래스로도 이용할 수 있음

```tsx
interface User {
  name: string;
  id: number;
}

class UserAccount {
  name: string;
  id: number;

  constructor(name: string, id: number) {
    this.name = name;
    this.id = id;
  }
}

const user: User = new UserAccount("Murphy", 1);
```

<br>

### Parameter 와 Return 값에 Type 지정하기

```tsx
function deleteUser(user: User) {
  // ...
}

function getAdminUser(): User {
  //...
}
```

<br>

### Type 여러개 지정하기

```tsx
type MyBool = true | false;
```

```tsx
function getLength(obj: string | string[]) {
  return obj.length;
}
```

<br>

### Usecase

- 주로 String or Numbeer로 Type을 Customize함

```tsx
type WindowStates = "open" | "closed" | "minimized";
type LockStates = "locked" | "unlocked";
type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;
```

<br>

### Typeof로 Type 반환

```tsx
function wrapInArray(obj: string | string[]) {
  if (typeof obj === "string") {
    return [obj];

(parameter) obj: string
  }
  return obj;
}
```

- string typeof s === "string"
- number typeof n === "number"
- boolean typeof b === "boolean"
- undefined typeof undefined === "undefined"
- function typeof f === "function"
- array Array.isArray(a)

```tsx
function wrapInArray(obj: string | string[]) {
  if (typeof obj === "string") {
    return [obj];

(parameter) obj: string
  }
  return obj;
}
```

<br>

### Generic

Array가 가장 일반적임

```tsx
type StringArray = Array<string>;
type NumberArray = Array<number>;
type ObjectWithNameArray = Array<{ name: string }>;
```

Object를 이용한 Generic

```tsx
interface Backpack<Type> {
  add: (obj: Type) => void;
  get: () => Type;
}

// This line is a shortcut to tell TypeScript there is a
// constant called `backpack`, and to not worry about where it came from.
declare const backpack: Backpack<string>;

// object is a string, because we declared it above as the variable part of Backpack.
const object = backpack.get();

// Since the backpack variable is a string, you can pass a string to the add function.
backpack.add("23");
```

### 구조적인 시스템

- Object의 property와 type이 같으면 굳이 그 타입으로 지정하지 않아도 호환이 됨

```tsx
interface Point {
  x: number;
  y: number;
}

function logPoint(p: Point) {
  console.log(`${p.x}, ${p.y}`);
}

// logs "12, 26"
const point = { x: 12, y: 26 };
logPoint(point);
```

- Type의 구조가 다른 objct의 부분집합이라고 하더라도 정상 작동함

```tsx
const point3 = { x: 12, y: 26, z: 89 };
logPoint(point3); // logs "12, 26"

const rect = { x: 33, y: 3, width: 30, height: 80 };
logPoint(rect); // logs "33, 3"
```

- 클래에서도 마찬가지

```tsx
class VirtualPoint {
  x: number;
  y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

const newVPoint = new VirtualPoint(13, 56);
logPoint(newVPoint); // logs "13, 56"
```
