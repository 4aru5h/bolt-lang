# bolt-lang

A toy dynamically typed programming language built from scratch in TypeScript. I built this to understand how lexers, operator precedence climbing, and AST tree-walking interpreters work under the hood.

It features an in-browser playground powered by Monaco Editor and runs inside a Web Worker sandbox with terminal streaming.

- **Interactive Playground:** [boltlang.vercel.app](https://boltlang.vercel.app)
- **Alternative Mirror:** [4aru5h.github.io/bolt-lang](https://4aru5h.github.io/bolt-lang/)

---

## Example Code

```bolt
def factorial(n) {
    if n <= 1 {
        give 1;
    }
    give n * factorial(n - 1);
}

emit("Factorial of 5:");
emit(factorial(5));

for i in 0..3 {
    emit(i);
}
```

See [docs/language.md](docs/language.md) for the full syntax and standard library guide (types, loops, array methods, and built-ins).

---

## How It Works

```text
Source Code
    │
    ▼
[Lexer / Tokenizer]        Character scanning, escape sequences, line/column tracking
    │
    ▼
[Recursive Descent Parser] Operator precedence climbing, AST node generation
    │
    ▼
[Abstract Syntax Tree]     Typed AST node representations with source positions
    │
    ▼
[Tree-Walking Interpreter] Scope environment chains, dynamic evaluation, safety step limits
    │
    ▼
[Web Worker Sandbox]       Isolated in-browser execution with real-time terminal output
```

---

## Development

```bash
# Install dependencies
npm install

# Run Vitest unit & integration test suite
npm test

# Start local playground server
npm run dev
```

---

## License

Distributed under the [MIT License](LICENSE).
