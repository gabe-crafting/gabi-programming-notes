---
links: []
title: Typescript
navigation:
  icon: i-nonicons-typescript-16
---

## Fundamentals

::card-group{.w-full}
  :::card
  ### Basic primitive types
  
  ```ts
  let str: string = "hello"
  let num: number = 42
  let bool: boolean = true
  let n: null = null
  let u: undefined = undefined
  let v: void = undefined // used for functions with no return
  let a: any = "anything" // disables type checking (avoid)
  let unk: unknown = 123 // safer alternative to any
  let nev: never = (() => { throw new Error("no return") })() // function never returns
  ```
  :::

  :::card
  ### Type inference and assertions
  
  ```ts
  let x = 5                 // inferred as number
  let y = x as number       // assertion (force treat as number)
  let z = <string>"text"    // JSX-incompatible assertion syntax
  let safe = maybeValue!    // non-null assertion (trust it's not null)
  ```
  
  ### Unions & Intersections, literal types
  
  ```ts
  type Status = "success" | "error" | "loading" // literal union
  type User = { name: string; age?: number }
  type Employee = User & { id: number }         // intersection merges types
  ```
  :::

  :::card
  ### Function typing
  
  ```ts
  function add(a: number, b: number): number {
    return a + b
  }
  
  const log = (msg: string): void => console.log(msg) // no return value
  
  // Function overloads for multiple input types
  function overload(a: string): string
  function overload(a: number): number
  function overload(a: any): any { return a }
  ```
  :::

  :::card
  ### Enums
  
  ```ts
    enum Direction { // numeric enum (auto-incremented)
    Up, // 0
    Down, // 1
    Left = 10, // explicit value
    Right // 11
  }
  
  enum Color { // string enum
    Red = "RED",
    Green = "GREEN",
    Blue = "BLUE"
  }
  ```
  :::
::

## Advanced Type System

Key points

- Generics + keyof/extends = flexible, type-safe APIs.
- Conditional + infer = extract pieces of types.
- Utility types reduce boilerplate; build your own when needed.

```ts
  // --- Generics (reusable type parameters)
  function identity<T>(v: T): T { return v }        // generic function
  type Box<T> = { value: T }                         // generic type

  // --- Constraints & keyof
  function pluck<T, K extends keyof T>(obj: T, key: K) {
    return obj[key]                                  // K restricted to object keys
  }

  // --- Utility built-ins (quick reference)
  type MyPartial<T> = Partial<T>                     // all props optional
  type MyRequired<T> = Required<T>                   // all props required
  type MyReadonly<T> = Readonly<T>                   // props readonly
  type MyPick<T, K extends keyof T> = Pick<T, K>     // select fields
  type MyOmit<T, K extends keyof T> = Omit<T, K>     // exclude fields
  type MyRecord<K extends keyof any, T> = Record<K, T>

  // --- Conditional types & infer
  type IsString<T> = T extends string ? true : false
  type FnReturn<T> = T extends (...a: any) => infer R ? R : never

  // --- Mapped & template literal types
  type Nullable<T> = { [P in keyof T]: T[P] | null } // make props nullable
  type EventName<T extends string> = `${T}Changed`    // template literal type

```

## Type Narrowing & Guards

Key points

- Use discriminants (literal kind fields) for exhaustive checks.
- Custom predicates help narrow complex types.

```ts
// --- Primitive guards
function format(v: string | number) {
  if (typeof v === "string") return v.toUpperCase()   // string branch
  return v.toFixed(2)                                  // number branch
}

// --- instanceof / Array.isArray
if (value instanceof Date) { /* Date-specific */ }
if (Array.isArray(x)) { /* array-specific */ }

// --- Custom type predicate
function isString(v: any): v is string {
  return typeof v === "string"
}
if (isString(maybe)) { /* TS knows maybe is string here */ }

// --- Discriminated union (recommended pattern)
type Shape =
  | { kind: "circle"; radius: number }
  | { kind: "rect"; width: number; height: number }

function area(s: Shape) {
  switch (s.kind) {
    case "circle": return Math.PI * s.radius ** 2
    case "rect": return s.width * s.height
  }
}
```
