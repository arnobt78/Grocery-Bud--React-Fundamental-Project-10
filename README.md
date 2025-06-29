# Grocery Bud - React Fundamental Project 10

<img width="534" alt="Screenshot 2025-02-09 at 15 43 05" src="https://github.com/user-attachments/assets/b3e82528-8e1d-4838-a58c-4d7ae967e68f" />

---

Grocery Bud is a beginner-friendly React application for managing a grocery list. It demonstrates essential React concepts, such as state management, component architecture, local storage integration, and user feedback via notifications. This project is ideal for learners who want to understand how to build CRUD (Create, Read, Update, Delete) applications with React, and it serves as a stepping stone for more complex apps.

- **Live-Demo:** https://grocery-bud-arnob.netlify.app/

---

## Table of Contents

- [Project Summary](#project-summary)
- [Features](#features)
- [Project Structure](#project-structure)
- [Installation & Getting Started](#installation--getting-started)
- [Components Walkthrough](#components-walkthrough)
- [Functionality & Flow](#functionality--flow)
- [Local Storage: How It Works](#local-storage-how-it-works)
- [Notifications: React-Toastify](#notifications-react-toastify)
- [Example Code Snippets](#example-code-snippets)
- [Technologies Used](#technologies-used)
- [Learning Outcomes & Keywords](#learning-outcomes--keywords)
- [Conclusion](#conclusion)

---

## Project Summary

Grocery Bud is a simple yet powerful grocery list manager built with React. It allows users to:

- Add, edit, and remove grocery items.
- Mark items as completed.
- Receive real-time notifications for actions.
- Persist the list in the browser's local storage so data isn’t lost on refresh.

This project is a great practical exercise for both beginners and intermediate React developers. It covers state management, component communication, managing side effects, and integrating 3rd-party libraries.

---

## Features

- Add items to the grocery list.
- Mark items as completed (with visual feedback).
- Remove items from the list.
- List persists in local storage between sessions.
- Real-time notifications for adding, removing, or submitting empty items.

---

## Project Structure

A typical project structure for Grocery Bud might look like this:

```
Grocery-Bud--React-Fundamental-Project-10/
├── public/
│   └── index.html
├── src/
│   ├── App.jsx
│   ├── index.js
│   ├── components/
│   │   ├── Form.jsx
│   │   ├── Items.jsx
│   │   └── SingleItem.jsx
│   ├── styles/
│   │   └── main.css
│   └── utils/
│       └── getLocalStorage.js
├── package.json
└── README.md
```

**Key Files & Folders:**
- `App.jsx`: Main component managing global state and orchestration.
- `components/Form.jsx`: Handles user input for new items.
- `components/Items.jsx`: Maps and renders the list of grocery items.
- `components/SingleItem.jsx`: Represents an individual grocery item.
- `utils/getLocalStorage.js`: Utility for local storage interactions.

---

## Installation & Getting Started

1. **Clone the repository:**

   ```sh
   git clone https://github.com/arnobt78/Grocery-Bud--React-Fundamental-Project-10.git
   cd Grocery-Bud--React-Fundamental-Project-10
   ```

2. **Install dependencies:**

   ```sh
   npm install
   ```

3. **Run the development server:**

   ```sh
   npm run dev
   ```

   The app will typically run at `http://localhost:5173/` (or as specified in the terminal).

---

## Components Walkthrough

### App.jsx

- Stores the main `items` state using `useState`.
- Handles adding, removing, completing, and editing items.
- Passes functions and state as props to child components.
- Handles local storage persistence.

### Form.jsx

- Renders an input and a submit button.
- On submission, calls `handleSubmit` from props to add a new item.

### Items.jsx

- Receives the items array as a prop.
- Maps through items, rendering each with `SingleItem`.

### SingleItem.jsx

- Displays the item’s name, a checkbox for completion, and a remove button.
- Uses `isChecked` state to manage local visual feedback.
- Calls parent functions for removal or completion.

---

## Functionality & Flow

1. **Adding Items:**  
   - User types in the form and submits.
   - New item is created with a unique id and added to the `items` state.
   - List auto-updates and persists to local storage.
   - Notification appears.

2. **Marking as Completed:**  
   - User checks the box next to an item.
   - The item's `completed` flag updates in state and local storage.
   - Visual style updates (e.g., strikethrough).

3. **Removing Items:**  
   - User clicks the remove (X) button.
   - Item is removed from state and local storage.
   - Notification appears.

---

## Local Storage: How It Works

Grocery Bud uses the browser's `localStorage` to save the grocery list between sessions.

**Saving Data:**
```js
localStorage.setItem('groceryList', JSON.stringify(items));
```

**Retrieving Data:**
```js
const items = JSON.parse(localStorage.getItem('groceryList')) || [];
```

**Example:**
```js
const user = {
  name: "John",
  age: 30,
};
localStorage.setItem("user", JSON.stringify(user));
const storedUser = JSON.parse(localStorage.getItem("user"));
console.log(storedUser.name); // 'John'
```

---

## Notifications: React-Toastify

This project uses [react-toastify](https://fkhadra.github.io/react-toastify/introduction) to show alerts for actions like:

- Adding a new item
- Attempting to submit an empty form
- Removing an item

**Example:**
```js
import { toast } from 'react-toastify';
toast.success('Item added!');
toast.error('Please enter a value!');
toast.info('Item removed.');
```

---

## Example Code Snippets

### Adding an Item

```jsx
const handleSubmit = (e) => {
  e.preventDefault();
  if (!inputValue) {
    toast.error('Please enter a value!');
    return;
  }
  const newItem = { id: uuidv4(), name: inputValue, completed: false };
  setItems([...items, newItem]);
  toast.success('Item added!');
};
```

---

### Removing an Item

```jsx
const removeItem = (id) => {
  setItems(items.filter(item => item.id !== id));
  toast.info('Item removed.');
};
```

---

### Marking Item as Completed

```jsx
const toggleComplete = (id) => {
  setItems(items.map(item =>
    item.id === id ? { ...item, completed: !item.completed } : item
  ));
};
```

---

## Technologies Used

- **React** (Functional components, Hooks)
- **JavaScript (ES6+)**
- **React-Toastify** (for notifications)
- **CSS** (styling)
- **Vite** (recommended for fast React dev experience)
- **localStorage** (browser API)

---

## Learning Outcomes & Keywords

**Keywords:** React, CRUD, useState, useEffect, localStorage, component, props, state, notification, toast, hooks, Vite, beginner project

### What You’ll Learn

- How to manage and persist state in React applications.
- How to structure a small-to-medium React project.
- Building reusable components and organizing files.
- Integrating third-party libraries (react-toastify).
- Working with browser APIs (localStorage).
- Best practices for user feedback and UX.

---

## Conclusion

Grocery Bud is a practical, hands-on React project that introduces core concepts needed for real-world web applications. It’s an excellent template for learning and teaching modern React fundamentals, file organization, component architecture, and user-centric features. Use this project as a foundation to build more advanced features such as authentication, API integration, or deployment.

Happy coding!

---
