# Understanding Generics in TypeScript

Generics are one of the most powerful features in TypeScript. They help developers create reusable and flexible code while maintaining strict type safety.

Without generics, developers often repeat similar logic for different data types.

---

# Problem Without Generics

Suppose we want functions for different types of arrays.

```ts
const createStringArray = (value: string): string[] => {
  return [value];
};

const createNumberArray = (value: number): number[] => {
  return [value];
};
```

The logic is identical, but the types are different.

This creates unnecessary duplication.

---

# Solution: Generics

Generics allow us to create one reusable function.

```ts
const createArray = <T>(value: T): T[] => {
  return [value];
};
```

`T` is called a generic type parameter.

It acts like a placeholder for any type.

---

# Using Generic Functions

## String Example

```ts
const stringArray = createArray<string>("Apple");
```

---

## Number Example

```ts
const numberArray = createArray<number>(100);
```

---

## Object Example

```ts
const userArray = createArray<{ name: string }>({
  name: "Ulfath",
});
```

---

# Why Generics Are Useful

## 1. Reusable Code

One function can work with multiple types.

---

## 2. Strong Type Safety

TypeScript still checks types correctly.

```ts
createArray<string>(100); // ❌ Error
```

---

## 3. Cleaner Applications

Less repeated code means cleaner projects.

---

# Generics in Components

Generics are also useful in reusable React components, tables, forms, and hooks.

They allow components to stay flexible while preserving strict typing.

---

#

Generics help developers build reusable, scalable, and type-safe applications.

They reduce duplication while keeping TypeScript smart enough to understand every data type correctly.