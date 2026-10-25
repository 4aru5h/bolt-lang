# bolt-lang

<p align="left">
  <img src="https://github.com/4aru5h/bolt-lang/actions/workflows/deploy.yml/badge.svg" alt="Deploy to GitHub Pages" />
  <img src="https://img.shields.io/badge/TypeScript-5.x-3178C6?logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Monaco_Editor-0.45-blue?logo=visualstudiocode&logoColor=white" alt="Monaco Editor" />
  <img src="https://img.shields.io/badge/Tests-Vitest-6E9F18?logo=vitest&logoColor=white" alt="Vitest" />
  <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License" />
</p>


Bolt is a toy programming language built from scratch in TypeScript, featuring an interactive web-based playground with a Monaco code editor, Web Worker sandboxing, and live terminal output.

It combines C-style curly braces and mandatory semicolons with dynamic typing and expression-oriented syntax.

- **Primary Playground:** [boltlang.vercel.app](https://boltlang.vercel.app)
- **Alternative Mirror:** [4aru5h.github.io/bolt-lang](https://4aru5h.github.io/bolt-lang/)
- **Repository:** [github.com/4aru5h/bolt-lang](https://github.com/4aru5h/bolt-lang)

---

## Architecture Pipeline

```text
Source Code
    |
    v
[Lexer / Tokenizer]        Character scanning, line/column tracking, escape sequences
    |
    v
[Recursive Descent Parser] Operator precedence climbing for binary expressions, AST generation
    |
    v
[Abstract Syntax Tree]     Typed AST node representations with source positions
    |
    v
[Tree-Walking Interpreter] Lexical environment chains, dynamic evaluation, step & recursion limits
    |
    v
[Web Worker & Playground]  Isolated thread execution in browser, terminal streaming
```

---

## Language Syntax & Features

### 1. Variables & Types
Bolt uses dynamic typing with types for integers, floats, strings, booleans, arrays, and `none`. Every statement terminates with a semicolon:

```bolt
let count = 10;
let ratio = 3.14159;
let greeting = "hello from bolt";
let active = true;
let empty = none;
```

### 2. Operators & Arithmetic
- `/` performs floating-point division (`5 / 2` evaluates to `2.5`).
- `//` performs integer floor division (`5 // 2` evaluates to `2`).
- `**` is exponentiation (`2 ** 8` evaluates to `256`), `%` is modulo.
- Logical operators: `and`, `or`, `not`.
- In-place compound assignments: `+=`, `-=`, `*=`, `/=`.

### 3. Functions & Return Statements
Functions are declared using `def`. Return values are passed using the `give` keyword:

```bolt
def add(a, b) {
    give a + b;
}

def factorial(n) {
    if n <= 1 {
        give 1;
    }
    give n * factorial(n - 1);
}

emit(add(15, 27));
emit(factorial(6));
```

### 4. Conditionals
Conditions do not require enclosing parentheses; curly braces are required:

```bolt
if score >= 90 {
    emit("Grade: A");
} elif score >= 80 {
    emit("Grade: B");
} elif score >= 70 {
    emit("Grade: C");
} else {
    emit("Grade: F");
}
```

### 5. Control Flow & Loops
Bolt supports five distinct loop forms with `break` and `continue`:

```bolt
# Exclusive range iteration (0 through 4)
for i in 0..5 {
    emit(i);
}

# Array traversal
for item in ["alpha", "beta", "gamma"] {
    emit(item);
}

# Fixed repetition
repeat 3 {
    emit("iteration");
}

# While loop
let n = 0;
while n < 3 {
    emit(n);
    n += 1;
}

# Unbounded loop with control flow
let counter = 0;
loop {
    counter += 1;
    if counter == 2 {
        continue;
    }
    if counter > 4 {
        break;
    }
    emit(counter);
}
```

### 6. Interactive Input & Built-in Functions
- `emit(x)`: Writes values directly to the stdout terminal.
- `input([prompt])`: Asynchronously halts interpreter execution to accept user input.
- `len(arr)`: Computes length of an array or string.
- `push(arr, item)` / `pop(arr)`: Array modification methods.
- `int(x)`, `float(x)`, `string(x)`: Explicit type coercion functions.

---

## Local Development & Testing

### 1. Install dependencies
```bash
npm install
```

### 2. Run the test suite
Executes unit and integration test suites covering the Lexer, Parser, and Interpreter via Vitest:
```bash
npm test
```

### 3. Start local development server
```bash
npm run dev
```

### 4. Build for production
```bash
npm run build
```

---

## Automated CI/CD

Pushes to the `main` branch trigger `.github/workflows/deploy.yml`, which automatically:
1. Checks out repository code.
2. Configures Node.js 20 with npm caching.
3. Installs dependencies and runs the Vitest test suite (`npm test`).
4. Compiles the production application bundle.
5. Deploys the static distribution to GitHub Pages.

---

## License

Distributed under the [MIT License](LICENSE).
