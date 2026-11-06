# Bolt Language Reference

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


