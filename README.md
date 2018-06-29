# TypeScript

Shared config for The Palmer Group's projects. 

There are 2 packages of interest.

- `tsconfig-palmerhq`: Shared base `tsconfig.json`
- `tslint-config-palmerhq`: Shared `tslint.json`

---

# Coding Guidelines

These guidelines are adapted from the TypeScript core's contributor coding guidelines.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Names](#names)
- [Exports](#exports)
- [Components](#components)
- [Types](#types)
- [`null` and `undefined`](#null-and-undefined)
- [General Assumptions](#general-assumptions)
- [Flags](#flags)
- [Comments](#comments)
- [Strings](#strings)
- [When to use `any`](#when-to-use-any)
- [Diagnostic Messages](#diagnostic-messages)
- [General Constructs](#general-constructs)
- [Style](#style)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Names

1. Use PascalCase for type names.
2. Do not use "I" as a prefix for interface names.
3. Use PascalCase for enum values.
4. Use camelCase for function names.
5. Use camelCase for property names and local variables.
6. Do not use "_" as a prefix for private properties.
7. Use whole words in names when possible.
8. Use `isXXXing` or `hasXXXXed` for variables representing states of things (e.g. `isLoading`, `hasCompletedOnboarding`).
10. Give folders/files/components/functions unique names. 

## Exports

1. Only use named exports. The only exception is the component is being code-split.

## Components 

1. 1 file per logical component (e.g. parser, scanner, emitter, checker).
2. If not kept in a separate folder, files with ".generated.*" suffix are auto-generated, do not hand-edit them.
3. Tests should be kept in the same directory with ".test.*" suffix
4. Filename should match the component name. Interfaces for React components should be called `<ComponentName>Props` and `<ComponentName>State`. The only exception is when writing a render prop. In this situation, you, the author, should call the interface for your component's props `<ComponentName>Config` and then the render prop interface `<ComponenName>Props` so it is easy for everyone else to use. 

## Types
1. Do not export types/functions unless you need to share it across multiple components.
2. Do not introduce new types/values to the global namespace.
3. Shared types should be defined in 'types.ts'.
4. Within a file, type definitions should come first.

## `null` and `undefined`
1. Use **undefined**. Do not use `null`. EVER. If null is used (like in legacy Redux code), it should be kept isolated from other code with selectors.

## General Assumptions
1. Consider objects like Nodes, Symbols, etc. as immutable outside the component that created them. Do not change them.
2. Consider arrays as immutable by default after creation.

## Flags
1. More than 2 related Boolean properties on a type should be turned into a flag.

## Comments
1. Use JSDoc style comments for functions, interfaces, enums, and classes.
2. Document crazy stuff. Always add `@see <url>` and the current date when referencing external resources, blog posts, tweets, snippets, gists, issues etc. 
3. Make note conditions upon which hacks and smelly code can be removed.

## Strings
1. Use single quotes for strings. Double quotes around JSX string props.
2. All strings visible to the user need to be localized (make an entry in diagnosticMessages.json).

## When to use `any`

1. If something takes you longer than 10 minutes to type or you feel the need to read through TS Advanced Types docs, you should take a step back and ask for help, or use `any`.
2. Custom typings of 3rd-party modules should be added to a `.d.ts` file in a `typings` directory. Document the date and version of the module you are typing at the top of the file.
3. Consider rewriting tiny modules in typescript if types are too hard to think through.

## Diagnostic Messages
1. Use a period at the end of a sentence.
2. Use indefinite articles for indefinite entities.
3. Definite entities should be named (this is for a variable name, type name, etc..).
4. When stating a rule, the subject should be in the singular (e.g. "An external module cannot..." instead of "External modules cannot...").
5. Use present tense.
6. Use active voice. 

## General Constructs

For a variety of reasons, we avoid certain constructs, and use some of our own. Among them:

1. Do not use `for..in` statements; instead, use `ts.forEach`, `ts.forEachKey` and `ts.forEachValue`. Be aware of their slightly different semantics.
2. Try to use `ts.forEach`, `ts.map`, and `ts.filter` instead of loops when it is not strongly inconvenient.

## Style

0. Use prettier and tslint.
1. Use arrow functions over anonymous function expressions.
2. Only surround arrow function parameters when necessary. <br />For example, `(x) => x + x` is wrong but the following are correct:
   1. `x => x + x`
   2. `(x,y) => x + y`
   3. `<T>(x: T, y: T) => x === y`
3. Always surround loop and conditional bodies with curly braces. Statements on the same line are allowed to omit braces.
4. Open curly braces always go on the same line as whatever necessitates them.
5. Parenthesized constructs should have no surrounding whitespace. <br />A single space follows commas, colons, and semicolons in those constructs. For example:
   1. `for (var i = 0, n = str.length; i < 10; i++) { }`
   2. `if (x < 10) { }`
   3. `function f(x: number, y: string): void { }`
6. Use a single declaration per variable statement <br />(i.e. use `var x = 1; var y = 2;` over `var x = 1, y = 2;`).
7. Use 2 spaces per indentation.
