# Typescript Cheat Sheet
Some useful practices that we may miss in our daily development.

## Snippets
New practices that I discovered when developing new scripts.

### [Type Utils](https://www.typescriptlang.org/docs/handbook/utility-types.html)

| Types | Opposite | Description | Possible Usage |
| - | - | - | - |
| Awaited | Get the return value from Promise | |
| Partial | Required | Make all the type as optional | Options in functions? |
| ReadOnly | | Make the object property as readonly. i.e. can't reassign the value | |
| Record | | | Constant file? | |
| Pick | Omit | Similar to lodash pick and omit function | Construct DTO? |
| **Exclude** | **Extract** | | |
| NonNullable | | Exclude the null and undefined from type | |
| Parameters | | Get the type of parameters of **Function** | |
| ConstructorParameters | | Get the type of parameters of **Class** | |
| ReturnType | | Get the type of return value of function | |
| InstanceType | | | |
| ThisParameterType | OmitThisParameter | | |
| ThisType | | | |
| Uppercase | Lowercase | | Good use for template literal |
| Capitalize | Uncapitalize | | Good use for template literal |

### [Using **Template Literal** in type annotation](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-1.html)

```ts
type Color = "red" | "blue";
type Quantity = "one" | "two";

type SeussFish = `${Quantity | Color} fish`;
// type SeussFish = "one fish" | "two fish" | "red fish" | "blue fish"
```

```ts
type VerticalAlignment = "top" | "middle" | "bottom";
type HorizontalAlignment = "left" | "center" | "right";
// Takes
//   | "top-left"    | "top-center"    | "top-right"
//   | "middle-left" | "middle-center" | "middle-right"
//   | "bottom-left" | "bottom-center" | "bottom-right"
declare function setAlignment(value: `${VerticalAlignment}-${HorizontalAlignment}`): void;
```

```ts
type PropEventSource<T> = {
    on<K extends string & keyof T>
        (eventName: `${K}Changed`, callback: (newValue: T[K]) => void ): void;
};
```

### [Key Remapping in Mapped Types](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-1.html)

```ts
type Options = {
  [K in "noImplicitAny" | "strictNullChecks" | "strictFunctionTypes"]?: boolean;
};
// same as
//   type Options = {
//       noImplicitAny?: boolean,
//       strictNullChecks?: boolean,
//       strictFunctionTypes?: boolean
//   };
```

### [Recursive Conditional Types](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-4-1.html#recursive-conditional-types)

### [Object destructuring with type](https://stackoverflow.com/questions/39672807/types-in-object-destructuring)

```ts
const {foo}: {foo: IFoo[]} = bar;
const foo: IFoo[] = bar.foo;$$
```

## History
Archived practices that have been engraved in my brain.
