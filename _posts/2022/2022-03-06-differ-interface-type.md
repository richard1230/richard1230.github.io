---
title: Differences between Interfaces and Type Aliases
date: 06-03-2022 
categories:
- Typescript 
tags:
- Typescript
---

Type aliases and interfaces are very similar, and in many cases you can choose between them freely. 

Almost all features of an **interface** are available in **type**, the key distinction is that a type cannot be re-opened to add new properties vs an interface which is always extendable.
### Type:
- Easy way to refer to the different properties + functions that a value has

#### Primitive Types
- number
- boolean
- void
- undefined
- string
- symbol
- null
#### Object Types
- functions
- arrays
- classes
- objects

### Interface:
- 
### Extending an interface
```typescript
    interface Animal {
        name:string
    }
    
    interface Bear extends Animal {
        honey: boolean
    }
    
    const bear = getBear()
    bear.name
    bear.honey
```

### Extending a type via intersections
```typescript
    type Animal = {
        name:string
    }
    
    type Bear = Animal & {
        honey: boolean
    }
    
    const bear = getBear()
    bear.name
    bear.honey
```

### Adding new fields to an existing interface
```typescript
    interface Window {
	title: string
}
  interface Window {
	ts: TypeScriptAPI
  }

```

### A type cannot be changed after being created
```typescript
  type Window = {
	title:string
}

  type Window = {
	ts: TypeScriptAPI
  }
// Error: Duplicate identifier 'Window'.

```