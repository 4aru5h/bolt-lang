# bolt-lang

A toy programming language written from scratch in TypeScript.

Includes a web playground with an embedded Monaco editor, execution in a Web Worker, and terminal output.

[Live Playground](https://bolt-sepia-six.vercel.app)

---

## Overview

Bolt combines dynamic typing with C-style curly braces and mandatory semicolons. Character scanning, AST generation, and tree-walk evaluation are implemented without external parser or compiler libraries.

### Pipeline

1. **Lexer:** Scans source code into tokens with line and column tracking.
2. **Parser:** Recursive descent parser with precedence climbing for binary expressions.
3. **Evaluator:** AST interpreter executing in an isolated Web Worker to prevent UI blocking.
4. **Playground:** Monaco code editor with live syntax highlighting and interactive console output.

---

## Development

```bash
npm install
npm run dev
```

Build for production:
```bash
npm run build
```

---

## License

MIT
