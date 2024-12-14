# L52: Type System Extensions for L5

An extension of the L5 programming language that adds support for type predicates, set operations on types, and additional type system features. Implements a sophisticated type system similar to TypeScript's type predicates.

## Features

- **Type Predicates**: Support for type predicate functions that help with type narrowing
- **Set Operations**: Implementation of union, intersection and difference operations on types
- **Extended Type System**: Support for `any` and `never` types
- **Complex Type Operations**: Support for normalized type expressions and disjunctive normal form

## Getting Started

### Prerequisites

- Node.js (LTS version recommended)
- npm (comes with Node.js)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/nissimbrami/L52-TypeSystem.git
cd L52-TypeSystem
```

2. Install dependencies:
```bash
npm install
```

3. Run tests:
```bash
npm test
```

## Project Structure

```
src/
├── L5/
│   ├── ast.ts           # Abstract Syntax Tree definitions
│   ├── TExp.ts          # Type Expression implementations
│   ├── typecheck.ts     # Type checking logic
│   └── parser.ts        # L5 language parser
└── test/
    └── L5/
        └── test.ts      # Test suite
```

## Type System Features

### Basic Types

- `any`: Represents all possible values
- `never`: Represents the empty set
- Standard L5 types (number, boolean, string, etc.)

### Complex Types

```typescript
// Union Type
(union T1 T2)           // T1 ∪ T2

// Intersection Type
(inter T1 T2)           // T1 ∩ T2

// Difference Type
(diff T1 T2)            // T1 \ T2
```

### Type Predicates

```typescript
// Type Predicate Example
(define (isNumber : (any -> is? number))
    (lambda ((x : any)) : is? number
        (number? x)))
```

## Implementation Details

### Type Operations

- Union types are normalized and ordered
- Intersection types are converted to disjunctive normal form
- Type differences handle special cases with `any` and `never`

### Type Checking

The type checker implements:
- Type predicate validation
- Set operation type rules
- Special handling for `if` expressions with type predicates

## Testing

```bash
# Run all tests
npm test

# Run specific test suite
npm test -- -t "type predicates"
```

## Project Requirements

- No additional libraries beyond those in package.json
- Maintains original configuration in package.json and tsconfig.json
- Tests must pass with provided test suite

## Technical Notes

- Type predicates only accept one argument
- Set operations follow standard set theory rules
- Type expressions are normalized after operations

## Author

Nissim Brami

## License

This project is licensed under the MIT License - see the LICENSE file for details.
