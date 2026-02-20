---
{"dg-publish":true,"permalink":"/interfaces-in-typescript/","tags":["interfaces"]}
---

## Merging

TypeScript can merge multiple declarations into a single one, enabling you to write multiple declarations for the same data structure and having them bundled together by the TypeScript Compiler during compilation as if they were a single type. In this section, you will see how this works and why it is helpful when using interfaces.

Interfaces in TypeScript can be re-opened; that is, multiple declarations of the same interface can be merged. This is useful when you want to add new fields to an existing interface.

For example, imagine that you have an interface named `DatabaseOptions` like the following one:

```
interface DatabaseOptions {
  host: string;
  port: number;
  user: string;
  password: string;
}
```

This interface is going to be used to pass options when connecting to a database.

Later in the code, you declare an interface with the same name but with a single `string` field called `dsnUrl`, like this one:

```
interface DatabaseOptions {
  dsnUrl: string;
}
```

When the TypeScript Compiler starts reading your code, it will merge all declarations of the `DatabaseOptions` interface into a single one. From the TypeScript Compiler point of view, `DatabaseOptions` is now:

```
interface DatabaseOptions {
  host: string;
  port: number;
  user: string;
  password: string;
  dsnUrl: string;
}
```

The interface includes all the fields you initially declared, plus the new field `dsnUrl` that you declared separately. Both declarations have been merged.

>[!QUOTE] **References**