

## Using the `$`, `$$`, and `$_` Shortcuts in Console

The `$`, `$$`, and `$_` shortcuts in the console provide quick ways to interact with and reference DOM elements or previously evaluated expressions using CSS selectors.

### Using `$` for Single Element Selection

1. **Selecting Single Elements**: Use the `$` shortcut followed by a CSS selector to select a single DOM element.

   Example:
   ```javascript
   // Select by ID
   const element = $('#myElement');
   
   // Select by class
   const elements = $('.myClass');
   
   // Select by element type
   const allParagraphs = $('p');
   ```

   The `$` is an alias for `document.querySelector()`.

### Using `$$` for Multiple Element Selection

1. **Selecting Multiple Elements**: Use the `$$` shortcut followed by a CSS selector to select multiple DOM elements.

   Example:
   ```javascript
   // Select all elements with a class
   const allElements = $$('.someClass');
   
   // Select all div elements
   const allDivs = $$('div');
   ```

   The `$$` is an alias for `document.querySelectorAll()`.

### Using `$_` for Referencing Last Expression

1. **Referencing Last Expression**: Use `$_` to reference the result of the last expression evaluated in the console.

   Example:
   ```javascript
   // Evaluate an expression
   const result = someFunction();
   
   // Reference the result in the next expression
   console.log($_); // This will log the value of 'result'
   ```

   The `$_` is particularly handy for quickly using the result of the last evaluated expression without needing to store it explicitly in a variable.

### Notes

- Ensure the page is fully loaded before using `$` or `$$` to access elements.
- `$` allows the selection of a single element while `$$` facilitates the selection of multiple elements.
- `$_` helps in referencing the result of the last evaluated expression in the console, streamlining debugging and testing workflows.

<br>
<br>
<br>
<br>

---
---


## Using `document.designMode` for Document Editing

The `document.designMode` property in JavaScript enables the editing mode for the entire document within the browser, allowing users to modify text content interactively.

### How to Use

1. **Enable Editing Mode**: Set `document.designMode = 'on'` to make the entire document editable.
   ```javascript
   // Enable document editing
   document.designMode = 'on';
   ```

2. **Disable Editing Mode**: Set `document.designMode = 'off'` to disable the editing mode.
   ```javascript
   // Disable document editing
   document.designMode = 'off';
   ```

### Functionality

- Enabling `document.designMode` to `'on'` allows users to interactively edit the text content displayed in the browser, similar to using a text editor.
- Disabling `document.designMode` returns the document to a non-editable state.

### Considerations

- Changes made while `designMode` is enabled are temporary and not automatically saved.
- Use caution when enabling `designMode` as it allows direct modification of the document's content.
- This feature is commonly used for creating in-browser text editors or enabling quick content edits within the displayed content.

### Notes

- Editing mode applies to the entire document, making all text content editable.
- Changes made in this mode are not persistent by default; additional logic is needed to handle and save edits if required.

<br>
<br>
<br>
<br>

---
---

### Using `addEventListener()` with the `once` Option

The `once` option in `addEventListener()` lets you run an event handler just once. It's perfect for scenarios where you want an action to be performed only the first time an event occurs.

#### Example:

```javascript
// Define the event handler function
function handleClick() {
  console.log('Button clicked!');
  // Additional actions can be performed here
}

// Get the button element
const button = document.getElementById('myButton');

// Add event listener with 'once' option
button.addEventListener('click', handleClick, { once: true });
```

- **`once: true`**: Setting `once` to `true` ensures the event handler (`handleClick`) runs only the first time the button is clicked.
- After the initial click, the event listener is automatically removed, ensuring it won't trigger again.

This simple usage of `once: true` eliminates the need to manually remove event listeners after they've been executed once, providing cleaner and more concise code.

For more information, check the [MDN documentation on `addEventListener()`](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener).


<br>
<br>
<br>
<br>

---
---

# Event Delegation with Bubbling and Capturing

263-video capture usage

### <a href="https://javascript.info/bubbling-and-capturing">JAVASCRIPT.INFO</a>

### <a href="https://javascript.info/bubbling-and-capturing#stopping-bubbling">JAVASCRIPT.INFO Stopping bubbling</a>


<br>
<br>
<br>
<br>

---
---

# Sync and async
## Synchronous (Sync) JavaScript:

- **What?** In synchronous JavaScript, code is executed line by line. Each line of code waits for the previous one to finish before executing.
- **Example:**

```javascript
console.log("Start");
console.log("Step 1");
console.log("Step 2");
console.log("End");
```

- **Result:** 
```
Start
Step 1
Step 2
End
```

In synchronous execution, the console logs are printed in the exact order they're written: "Start," "Step 1," "Step 2," and "End."

## Asynchronous (Async) JavaScript:

- **What?** In asynchronous JavaScript, code doesn't wait for tasks to finish before moving on. It can start a task and move to the next line without waiting for the task to complete.
- **Example (Using `setTimeout`):**

```javascript
console.log("Start");
setTimeout(() => {
  console.log("Async Step 1");
}, 2000);
console.log("Step 2");
console.log("End");
```

- **Result:** 
```
Start
Step 2
End
Async Step 1
```

In asynchronous execution with `setTimeout`, "Start" is logged first, followed by "Step 2" and "End" immediately. After a delay of 2 seconds, "Async Step 1" is logged. This delay does not pause the rest of the code execution.

Understanding sync and async is crucial in JavaScript for handling tasks like fetching data or performing operations that may take time, ensuring smoother performance and responsiveness in your code.
<br>
<br>
<br>
<br>

---
---
# Callback Functions 

## What is a Callback Function?

In JavaScript, a callback function is a function that is passed as an argument to another function and gets executed after a certain task is completed or an event occurs. It's commonly used in asynchronous operations, like handling responses from APIs or executing code after a timeout.

## How to Use Callback Functions?

### Example 1: Basic Usage

```javascript
// Define a function that takes a callback
function greet(callback) {
  console.log("Hello!");
  // Execute the callback function
  callback();
}

// Define a callback function
function sayGoodbye() {
  console.log("Goodbye!");
}

// Call the greet function and pass the callback
greet(sayGoodbye);
```

### Example 2: Asynchronous Operations

```javascript
// Simulating an asynchronous operation with setTimeout
function fetchData(callback) {
  setTimeout(function () {
    const data = "Some fetched data";
    // Execute the callback function with the fetched data
    callback(data);
  }, 2000); // Simulating a 2-second delay
}

// Define a callback function to handle fetched data
function processData(data) {
  console.log("Data received:", data);
}

// Call fetchData and pass the processData function as a callback
fetchData(processData);
```

## Summary

Callback functions are essential in JavaScript for handling asynchronous tasks or defining behavior that should occur after a certain action completes. They provide a way to create flexible and reusable code by passing functions as arguments to other functions.


---
---

## better example

```javascript
// Initial book list array
let bookList = [
  { title: "The Catcher in the Rye", author: "J.D. Salinger" },
  { title: "To Kill a Mockingbird", author: "Harper Lee" },
];

// Function to add a new book asynchronously
function addBook(title, author, callback) {
  setTimeout(function () {
    const newBook = { 
        title: title,
        author: author 
    }; 
    // Creating a book object
    bookList.push(newBook);
    callback();
  }, 3000); // Simulating a 3-second delay for the asynchronous operation
}

// Callback function to log the updated book list
function logBookList() {
  console.log("Updated Book List:");
  console.table(bookList);
}

// New book's title and author (you can get these dynamically)
const newTitle = "1984";
const newAuthor = "George Orwell";

// Adding a new book to the list asynchronously and logging the updated list
addBook(newTitle, newAuthor, logBookList);
```

This code defines the `addBook` function, which now takes `title` and `author` arguments along with a callback. Inside `addBook`, it creates a new book object using these arguments and adds it to the book list array after a delay. After the addition is done, it executes the callback function `logBookList` to log the updated book list. Adjust the `newTitle` and `newAuthor` variables to get the title and author dynamically if needed.

<br>
<br>
<br>
<br>

---
---

# Pure Functions

### What Are They?

Pure functions in JavaScript are functions that always produce the same output for the same input and have no side effects.

### Characteristics:

1. **Deterministic Output:** Given the same inputs, a pure function will always return the same output, like a math equation: `y = f(x)`.
2. **No Side Effects:** They don’t modify anything outside their scope—no changing global variables, modifying input parameters, or affecting anything else.

### Example:

```javascript
// Pure Function Example
function add(a, b) {
  return a + b;
}
```

In the `add` function, for the same `a` and `b` inputs, it consistently returns the same result without altering any external variables or state.

### Non-Examples (Impure Functions):

#### 1. Using Random Numbers:

```javascript
function impureRandomAdd(a) {
  return a + Math.random(); // Incorporating a random number
}
```

The `impureRandomAdd` function uses `Math.random()` which introduces randomness, leading to different results for the same input.

#### 2. Modifying Variable Outside Function:

```javascript
let result = 0;

function impureAdd(a) {
  result += a; // Modifies external state
  return result;
}
```

The `impureAdd` function modifies the `result` variable outside its scope, making it impure because it changes external state.

### Why Care?

- **Predictability:** Pure functions are predictable and easier to understand, debug, and test.
- **Avoiding Bugs:** They reduce unexpected side effects that can lead to bugs or issues in larger codebases.

### Benefits:

- **Testability:** Easier to test since they rely only on their inputs.
- **Reusability:** Encourages modular, reusable code.
- **Parallel Processing:** Easier to parallelize and optimize.

---

Understanding and using pure functions can promote more maintainable and reliable code, especially in functional programming paradigms.

<br>
<br>
<br>
<br>

---
---


# Global and Local Scope in JavaScript

### Global Scope
- **Description**: Think of it as the entire city where everyone can see and access the buildings and streets.
- **In JavaScript**: Variables declared outside of any function reside here. They're visible and usable by any part of your code.

### Local Scope
- **Description**: Picture neighborhoods within the city, each with its own houses and rules.
- **In JavaScript**: Variables declared inside a function belong to that function's neighborhood. They're only visible and usable within that specific function.

#### Example:

```javascript
// Global scope
let cityHall = 'Big Building';

function exploreNeighborhood() {
  // Local scope inside the function
  let house = 'Cozy Cottage';
  console.log(cityHall); // Accessible because it's in the global scope
  console.log(house); // Accessible because it's in the local scope
}

console.log(cityHall); // Accessible
// console.log(house); // Not accessible, in a different scope
exploreNeighborhood(); // Calls the function
```

Understanding these scopes helps control how variables are accessed and used within your JavaScript code.

<br>
<br>
<br>
<br>

---
---


# Higher-Order Functions (HOFs) in JavaScript

### Definition:
- **What are HOFs?**: Functions that either take a function as an argument or return a function, treating functions as values.

### Examples and Use Cases:
- **1. Functions as Arguments**: Pass a function as an argument to another function.
  ```javascript
  function doOperation(operation, a, b) {
    return operation(a, b);
  }

  function add(a, b) {
    return a + b;
  }

  function subtract(a, b) {
    return a - b;
  }

  console.log(doOperation(add, 5, 3)); // Output: 8
  console.log(doOperation(subtract, 10, 4)); // Output: 6
  ```

- **2. Functions as Return Values**: Return a function from another function.
  ```javascript
  function greeter(greeting) {
    return function(name) {
      console.log(`${greeting}, ${name}!`);
    };
  }

  const greetHello = greeter('Hello');
  greetHello('Alice'); // Output: Hello, Alice!

  const greetGoodMorning = greeter('Good morning');
  greetGoodMorning('Bob'); // Output: Good morning, Bob!
  ```

### Benefits:
- **Code Reusability**: Allows the reuse of functions, making code more concise and maintainable.
- **Abstraction**: Helps in abstracting certain functionalities to make code more modular and flexible.

### Considerations:
- **Readability**: While powerful, excessive nesting of functions can reduce code readability. Use HOFs judiciously.

### Summary:
Higher-Order Functions in JavaScript empower you to treat functions as values. Whether passing functions as arguments or returning functions from other functions, they enhance code reusability and abstraction. However, maintain code readability by using them thoughtfully.
