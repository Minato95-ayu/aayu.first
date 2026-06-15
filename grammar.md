# Aayu Language Grammar v0.1

This is the minimal grammar for Aayu v0.1.

## Structure

Aayu programs are sequences of statements. Every statement ends with a period `.`. Blocks use the `end.` keyword to signify termination.

## Statements

### Use
```
"use" identifier "."
```
- Example: `use math.`

### Variables
```
type identifier "is" expression "."
```
- Example: `number age is 18.`
- Example: `text name is "Ayush".`

### Records
```
"record" identifier "."
  { identifier }
"end" "."
```
- Example:
  ```aayu
  record Student.
      name
      age
  end.
  ```

### Instances
```
identifier identifier "is" "."
  { identifier expression }
"end" "."
```
- Example:
  ```aayu
  Student student1 is.
      name "Ayush"
      age 20
  end.
  ```

### Show
```
"show" expression "."
```
- Example: `show a + b.`

### Lists
```
"list" identifier "is" "."
  [expressions]
"end" "."
```
- Example:
  ```aayu
  list students is.
      "Ayush"
      "Rahul"
      "Aman"
  end.
  ```

### If
```
"if" expression [ "is" ] comparator expression "."
  [statements]
"end" "."
```
- Example: 
  ```aayu
  if age greater than 18.
      show "Adult".
  end.
  ```

### Repeat
```
"repeat" expression "times" "."
  [statements]
"end" "."
```
- Examples: 
  ```aayu
  repeat 5 times.
      show "Hello".
  end.
  ```

### For Each
```
"for" "each" identifier "in" expression "."
  [statements]
"end" "."
```
- Example:
  ```aayu
  for each student in students.
      show student.
  end.
  ```

### Task
```
"task" identifier [ "with" identifier { "and" identifier } ] "."
  [statements]
"end" "."
```
- Examples:
  ```aayu
  task greet.
      show "Hello".
  end.
  ```
  ```aayu
  task add with first and second.
      result is first + second.
  end.
  ```

### Run
```
"run" identifier [ "with" expression { "and" expression } ] "."
```
- Examples: 
  - `run greet.`
  - `run add with 10 and 20.`

### Result
```
"result" "is" expression "."
```
- Example: `result is first + second.`

## Expressions

Statements can be:
- Variable Declarations (`number`, `text`)
- Outputs (`show`)
- Control Flow (`if`)
- Loops (`repeat`, `for each`)
- Tasks (`task`)
- Module Imports (`use`)
- List Declarations (`list`)
- Record Declarations (`record`)
- Instance Declarations (`TypeName instance_name is .`)
- Mathematical operations (`+`, `-`, `*`, `/`)
- Comparisons (`greater than`, `less than`, `equal to`)
- Literals (Numbers, Text)
- Variables (`identifier`)
- Task Execution (`run identifier`)
- Property Access (`identifier of identifier`)

### Comparators
Used within `if` conditions. The AST maps these to standard symbols (`>`, `<`, `==`).
- `greater than`
- `less than`
- `equal to`
*(Reserved: "greater than or equal to", "less than or equal to", "not equal to")*

Example of valid math: `10 + 20` or `age * 5`
