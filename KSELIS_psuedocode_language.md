## **KSELIS Psuedocode Language Overview**

This language is an interpreted, dynamically typed, pseudo-code-like language designed for educational purposes. It emphasizes readability, using English-like syntax (e.g., `SET x TO 10`) over traditional C-style operators (e.g., `x = 10`).

### **Basic Syntax and Data Types**

* **Comments:** Begin with `#` and run to the end of the line.
* **Strings:** Enclosed in double `"` or single `'` quotes.
* **Numbers:** Integers and floats (e.g., `42`, `3.14`).
* **Booleans:** `TRUE` or `FALSE`.
* **Collections:** Lists, Sets, and Tuples.

---

## **1. Variables and Data Structures**

### **Variable Assignment**

Variables are created and updated using the `SET ... TO ...` syntax.

```text
# Basic assignment
SET greeting TO "Hello, World!"
SET age TO 25
SET isReady TO TRUE

```

### **Collections**

You can create collections using literal syntax or the `CREATE` keyword.

**Lists**
Lists are ordered, mutable collections. You can access and assign elements by their zero-based index.

```text
SET scores TO [10, 20, 30]
SET emptyList TO CREATE LIST

# Modifying lists
APPEND 40 TO scores
REMOVE 20 FROM scores

# Index assignment
SET scores[0] TO 99

```

**Sets and Tuples**
Sets (unordered, unique elements) and Tuples (ordered, typically immutable in logic though treated as lists structurally) must be instantiated using `CREATE`.

```text
SET mySet TO CREATE SET_DATA
APPEND "apple" TO mySet

SET myTuple TO CREATE TUPLE

```

### **Indexing and Slicing**

Collections and strings support zero-based indexing and slicing `[start:end]`. Negative indexing is supported (e.g., `-1` is the last element).

```text
SET myData TO [10, 20, 30, 40, 50]

PRINT myData[1]       # Outputs: 20
PRINT myData[-1]      # Outputs: 50
PRINT myData[1:4]     # Outputs: [20, 30, 40]

```

---

## **2. Operators**

* **Arithmetic:** `+` (Add/Concatenate), `-` (Subtract), `*` (Multiply), `/` (Divide), `//` (Integer Division), `%` (Modulo).
* **Comparison:** `==` (Equal), `!=` (Not Equal), `<` (Less than), `>` (Greater than), `<=` (Less/Equal), `>=` (Greater/Equal).
* **Logical:** `AND`, `OR`, `NOT`.

```text
SET result TO (10 + 5) * 2 // 3
SET isValid TO (age >= 18) AND NOT FALSE

```

---

## **3. Control Flow**

### **Conditionals (IF / ELSE IF / ELSE)**

Conditionals use `IF ... THEN` blocks, closing with `ENDIF`.

```text
IF score >= 90 THEN
    PRINT "Grade: A"
ELSE IF score >= 80 THEN
    PRINT "Grade: B"
ELSE
    PRINT "Grade: C"
ENDIF

```

### **While Loops**

Executes a block of code as long as the condition evaluates to `TRUE`.

```text
SET count TO 0
WHILE count < 5
    PRINT count
    SET count TO count + 1
ENDWHILE

```

### **For Loops**

The language supports two types of `FOR` loops: range-based and collection-based.

**Range Loop (`FOR ... FROM ... TO`)**

```text
FOR i FROM 1 TO 5
    PRINT i
ENDFOR

```

**Iterator Loop (`FOR EACH ... IN`)**
Iterates over elements in a List, Set, or Tuple.

```text
SET fruits TO ["Apple", "Banana", "Cherry"]
FOR EACH fruit IN fruits
    PRINT fruit
ENDFOR

```

### **Loop Control**

* `BREAK`: Immediately exits the nearest loop.
* `CONTINUE`: Skips the rest of the current loop iteration and moves to the next.

---

## **4. Functions**

Functions are defined using `FUNCTION` and `ENDFUNCTION`. They can take parameters and return values.

```text
FUNCTION calculateArea(width, height)
    SET area TO width * height
    RETURN area
ENDFUNCTION

SET myArea TO calculateArea(5, 10)
PRINT myArea

```

---

## **5. Input and Output**

### **Output**

Use the `PRINT` statement to display text or variable contents.

```text
PRINT "The application has started."

```

### **Input**

Prompts the user for data using built-in expressions.

* `INPUT_TEXT(prompt)`: Returns a string.
* `INPUT_NUM(prompt)`: Returns a parsed float/number.

```text
SET userName TO INPUT_TEXT("What is your name?")
SET userAge TO INPUT_NUM("Enter your age:")

```

---

## **6. Built-in Native Functions**

The language comes with standard library functions pre-injected into the global environment:

* **`LENGTH(collection)`**: Returns the size/length of a string, list, tuple, or set.
* **`SUM(list)`**: Returns the sum of all numbers in a list.
* **`MIN(list)` / `MAX(list)**`: Returns the smallest/largest number in a list.
* **`CONTAINS(collection, item)`**: Returns `TRUE` if the item is inside the list/set/string.
* **`INDEXOF(collection, item)`**: Returns the numeric index of an item, or `-1` if not found.
* **`RANDOM_INT(min, max)`**: Generates a random integer between min and max (inclusive).
* **`TO_STRING(value)`**: Casts a value to a String.
* **`TO_NUM(value)`**: Casts a string to a Number.
* **`DATE()`**: Returns the current system date as a string ("DD/MM/YYYY").
* **`TIME()`**: Returns the current system time as a string ("HH:MM:SS").
* **`TCOMP(str)` / `SCOMP(str)**`: Returns formatted strings for Time and Space complexity (e.g., `TCOMP("O(N)")` yields `"Time Complexity: O(N)"`).

---

## **7. Testing and Debugging**

### **Trace Mode**

Allows line-by-line debugging output in the console.

```text
TRACE ON
SET x TO 5
TRACE OFF

```

### **Assertions**

Used to test conditions. If the condition is `FALSE`, the program throws an immediate runtime error.

```text
SET mathResult TO 5 + 5
ASSERT mathResult == 10  # Program continues silently if true

```

---

## **Complete Keyword Glossary**

Here is a detailed explanation of every reserved keyword in the language's lexer:

| Keyword | Description |
| --- | --- |
| **`SET`** | Starts a variable assignment or array-index assignment (e.g., `SET x TO 5`). |
| **`TO`** | Used in conjunction with `SET` to denote the value being assigned. Also used in `FOR ... FROM ... TO` loops and `APPEND ... TO`. |
| **`PRINT`** | Outputs the evaluated expression to the terminal. |
| **`IF`** | Starts a conditional block. Evaluates a boolean expression. |
| **`THEN`** | Separates the condition from the consequent execution block in an `IF` or `ELSE IF` statement. |
| **`ELSE`** | Provides a fallback execution block if the preceding `IF` or `ELSE IF` condition fails. |
| **`ENDIF`** | Closes an `IF` statement block. |
| **`WHILE`** | Starts a loop that continues as long as a specified condition remains `TRUE`. |
| **`ENDWHILE`** | Closes a `WHILE` loop block. |
| **`FOR`** | Starts an iteration block. Can be used as a range loop or an iterator loop. |
| **`EACH`** | Used in conjunction with `FOR` to loop through elements of a collection (`FOR EACH x IN y`). |
| **`IN`** | Specifies the collection being iterated over in a `FOR EACH` loop. |
| **`ENDFOR`** | Closes a `FOR` loop block. |
| **`FROM`** | Specifies the starting integer in a range-based loop (`FOR i FROM 1 TO 5`). |
| **`CREATE`** | Instantiates a new, empty data structure. Followed by `LIST`, `SET_DATA`, or `TUPLE`. |
| **`LIST`** | Used with `CREATE` to instantiate a new array/list. |
| **`SET_DATA`** | Used with `CREATE` to instantiate a new Set (collection of unique items). |
| **`TUPLE`** | Used with `CREATE` to instantiate a new Tuple. |
| **`APPEND`** | Adds an item to the end of a List or Set. Used as `APPEND x TO y`. |
| **`REMOVE`** | Deletes a specific item from a List or Set. Used as `REMOVE x FROM y`. |
| **`INPUT_TEXT`** | Pauses execution and prompts the user for text input. |
| **`INPUT_NUM`** | Pauses execution and prompts the user for numerical input. |
| **`AND`** | Logical operator: Returns `TRUE` only if both left and right expressions are truthy. |
| **`OR`** | Logical operator: Returns `TRUE` if at least one of the expressions is truthy. |
| **`FUNCTION`** | Declares a user-defined, reusable block of code. |
| **`ENDFUNCTION`** | Closes a function declaration. |
| **`RETURN`** | Exits a function immediately and passes the specified value back to the caller. |
| **`BREAK`** | Immediately terminates the innermost loop (`WHILE` or `FOR`). |
| **`CONTINUE`** | Skips the remaining code in the current loop iteration and proceeds to the next iteration. |
| **`TRUE`** | A Boolean literal representing truth. |
| **`FALSE`** | A Boolean literal representing falsehood. |
| **`NOT`** | Unary logical operator that inverts a boolean value. |
| **`TRACE`** | Diagnostic tool. Used with `ON` or `OFF` to toggle execution step logging in the terminal. |
| **`ON`** | Activates trace logging. |
| **`OFF`** | Deactivates trace logging. |
| **`ASSERT`** | Evaluates an expression. If it is `FALSE`, the interpreter throws an error and aborts the script. |
