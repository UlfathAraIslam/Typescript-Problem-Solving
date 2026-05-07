# How `Pick` and `Omit` Keep TypeScript Code DRY

In large applications, developers often work with large interfaces containing many properties. Sometimes we only need a few properties, or we want to exclude some properties.

Instead of rewriting interfaces repeatedly, TypeScript provides two useful utility types:

- `Pick`
- `Omit`

These help keep code DRY (Don't Repeat Yourself).

---

# The Problem Without Utility Types

Imagine a user interface:

```ts
interface User {
  id: number;
  name: string;
  email: string;
  password: string;
}
```

Now suppose we want another type for displaying public user information.

Without utility types:

```ts
interface PublicUser {
  id: number;
  name: string;
  email: string;
}
```

This duplicates code.

If the original interface changes later, we must update multiple interfaces manually.

---

# Using `Pick`

`Pick` allows us to select specific properties from an existing interface.

```ts
type PublicUser = Pick<User, "id" | "name" | "email">;
```

Now TypeScript creates a new type using only selected properties.

---

# Benefits of `Pick`

- Reduces duplication
- Keeps code cleaner
- Automatically updates if the main interface changes

---

# Using `Omit`

`Omit` creates a type by removing specific properties.

```ts
type SafeUser = Omit<User, "password">;
```

This creates:

```ts
{
  id: number;
  name: string;
  email: string;
}
```

---

# Real-Life Example

Imagine an admin panel:

```ts
interface Product {
  id: number;
  name: string;
  price: number;
  createdAt: string;
}
```

For creating a new product, we may not need `id` or `createdAt`.

```ts
type CreateProduct = Omit<Product, "id" | "createdAt">;
```

This avoids rewriting the same fields.

---

# Keeping Code DRY

DRY means:

> “Don’t Repeat Yourself.”

`Pick` and `Omit` help developers:

- Reuse existing interfaces
- Avoid repeated code
- Improve maintainability
- Reduce bugs

---

# 

`Pick` and `Omit` are powerful utility types in TypeScript.

They allow developers to create specialized versions of interfaces without duplicating code. This keeps applications cleaner, easier to maintain, and more scalable.