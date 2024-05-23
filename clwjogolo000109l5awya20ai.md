---
title: "How to Create a To-Do List with React"
seoTitle: "React To-Do List Tutorial"
seoDescription: "Learn how to build a dynamic To-Do List using React, from setup to basic functionalities. Start organizing tasks efficiently!"
datePublished: Thu May 23 2024 20:00:27 GMT+0000 (Coordinated Universal Time)
cuid: clwjogolo000109l5awya20ai
slug: how-to-create-a-to-do-list-with-react
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/RLw-UC03Gwc/upload/6910dba92cfcfdb294bc6c5bd47a03ea.jpeg
tags: tutorial, css3, css, javascript, reactjs, javascript-framework, todolist, step-by-step

---

To-do lists are an essential tool for organizing day-to-day tasks. With React, one of the most popular JavaScript libraries for building user interfaces, we can create a dynamic and interactive To-Do List. In this tutorial, we'll guide you through the process of creating a simple To-Do List using React, from the initial setup to implementing basic functionalities.

## Prerequisites 💡

Before we dive into building our To-Do List with React, let's ensure that you have Node.js and npm installed on your machine. Here's how you can verify and install them if needed:

### Verifying Node.js and npm Installation

Open your terminal (**Command Prompt**, **PowerShell**, or **Terminal**) and run the following commands:

**To check the version of Node.js installed:**

```bash
node -v
```

**To check the version of npm installed:**

```bash
npm -v
```

If both commands return a version number, it means Node.js and npm are already installed on your machine.

### **Installing Node.js and npm**

If Node.js and npm are not installed or if the commands above don't return a version number, follow these steps to install them:

**Download the Installer**: Visit the official Node.js website at [nodejs.org](http://nodejs.org) and download the installer for your operating system (Windows, macOS, or Linux).

**Install Node.js**: Run the downloaded installer and follow the installation instructions. The installation process will automatically install both Node.js and npm.

**Verify Installation**: Once the installation is complete, open a new terminal window and run the `node -v` and `npm -v` commands again to verify that Node.js and npm are installed correctly.

## Step 1: Setting Up the Environment

Let's start by creating a new React application. Open your terminal and run the following command:

```bash
npx create-react-app todo-list
```

This will create a new folder named `todo-list` with the basic structure of the React project.

## Step 2: Project Structure

After creating the React application, navigate to the project directory and open it in your preferred code editor. Inside the `src` folder, you'll find the main project files. To keep our code organized, let's create three new folders: `components`, `pages`, and `styles`.

```plaintext
todo-list/
  ├── src/
  │   ├── components/
  │   ├── pages/
  │   └── styles/
```

## Step 3: Creating Components

Inside the `components` folder, create two new files: `TodoForm.js` and `TodoItem.js`. The `TodoForm` will be responsible for adding new tasks to the list, while `TodoItem` will be responsible for displaying each item in the task list.

### TodoItem.js

Let's start by implementing the `TodoItem`. Here's a basic example of the code for this component:

```javascript
// TodoItem.js - https://hashnode.com/@hugotav
import React from 'react'; //1

const TodoItem = ({ todo, toggleTodo }) => { //2
  const handleToggle = () => { //3
    toggleTodo(todo.id); //4
  };

  return ( //5, 6 e 7
    <div className={`todo-item ${todo.completed ? 'completed' : ''}`}>
      <input
        type="checkbox"
        checked={todo.completed}
        onChange={handleToggle}
      />
      <p>{todo.text}</p>
    </div>
  );
};

export default TodoItem; //8
```

1. `import React from 'react';`: This line imports the React library, which is necessary for creating React components.
    
2. `const TodoItem = ({ todo, toggleTodo }) => {`: This declares a functional component named TodoItem, which accepts two props: `todo` and `toggleTodo`. The `todo` prop represents an individual todo item, and the `toggleTodo` prop is a function used to toggle the completion status of the todo item.
    
3. `const handleToggle = () => {`: This defines a function named `handleToggle`, which will be called when the checkbox is clicked.
    
4. `toggleTodo(todo.id);`: This calls the `toggleTodo` function, passing the ID of the todo item as an argument. This function is responsible for toggling the completion status of the todo item.
    
5. ``<div className={`todo-item ${todo.completed ? 'completed' : ''}`}>``: This creates a element with a CSS class of "todo-item". If the todo item is completed (based on the completed property), the class "completed" will be added to the element, which can be used to apply styling indicating that the todo item is completed.
    
6. `<input type="checkbox" checked={todo.completed} onChange={handleToggle}/>`: This creates a checkbox input field. The checked attribute is set based on the completed property of the todo item. If the todo item is `completed`, the checkbox will be `checked`. The onChange event handler is set to call the `handleToggle` function when the checkbox is clicked.
    
7. `<p>{todo.text}</p>`: This displays the text content of the todo item inside a `<p>` element.
    
8. `export default TodoItem;`: This exports the TodoItem component so that it can be imported and used in other parts of the application.
    

### TodoForm.js

Now, let's implement the `TodoForm`. This component will have a text field for adding new tasks to the list.

```javascript
// TodoForm.js - https://hashnode.com/@hugotav
import React, { useState } from 'react'; //1

const TodoForm = ({ addTodo }) => { //2
  const [text, setText] = useState(''); //3

  const handleSubmit = (e) => { //4
    e.preventDefault();
    if (!text.trim()) return;
    addTodo(text);
    setText('');
  }

  return ( //5, 6 e 7
    <form onSubmit={handleSubmit}>
      <input 
        type="text" 
        value={text} 
        onChange={(e) => setText(e.target.value)} 
        placeholder="Add new task" 
      />
      <button type="submit">Add</button>
    </form>
  );
}

export default TodoForm; //8
```

1. `import React, { useState } from 'react';`: This line imports React and the `useState` hook from the React library. The `useState` hook is used to manage state within functional components.
    
2. `const TodoForm = ({ addTodo }) => {`: This declares a functional component named TodoForm, which accepts a prop named `addTodo`. This prop is a function used to add a new todo item to the list.
    
3. `const [text, setText] = useState('');`: This line uses the `useState` hook to create a state variable named `text`, which represents the value of the input field in the form. The initial state is an empty string. The `setText` function is used to update the value of `text`.
    
4. `const handleSubmit = (e) => { ... }`: This defines a function `handleSubmit` which is triggered when the form is submitted. It prevents the default form submission behavior, checks if the input field is not empty, adds the new todo item using the `addTodo` function, and then resets the input field to an empty string.
    
5. `<form onSubmit={handleSubmit}>`: This creates a form element with an `onSubmit` event handler set to `handleSubmit`, so that when the form is submitted, the `handleSubmit` function is called.
    
6. `<input type="text" value={text} onChange={(e) => setText(`[`e.target`](http://e.target)`.value)} placeholder="Add new task" />`: This creates a text input field. The value of the input is controlled by the `text` state variable. When the input value changes, the `onChange` event updates the `text` state using the `setText` function.
    
7. `<button type="submit">Add</button>`: This creates a submit button for the form.
    
8. `export default TodoForm;`: This exports the TodoForm component so that it can be imported and used in other parts of the application.
    

## Step 4: Implementing the Task List

Inside the `pages` folder, create a new file named `TodoPage.js`. This file will be responsible for managing the state of the task list and rendering the `TodoForm` and `TodoItem` components.

```javascript
// TodoPage.js  - https://hashnode.com/@hugotav

import React, { useState } from 'react';
import TodoForm from '../components/TodoForm'; // Importing TodoForm component from TodoForm.js file
import TodoItem from '../components/TodoItem'; // Importing TodoItem component from TodoItem.js file
import '../styles/TodoStyles.css'; // Importing CSS styles for TodoPage

// Declaring functional component TodoPage
const TodoPage = () => {
  // Declaring state variable 'todos' and function 'setTodos' using useState hook
  const [todos, setTodos] = useState([]); // Initial state is an empty array

  // Function to add a new todo item to the list
  const addTodo = (text) => {
    const newTodo = { id: Date.now(), text, completed: false }; // Creating a new todo object with unique ID, provided text, and initial completion status
    setTodos([...todos, newTodo]); // Updating the state by adding the new todo item to the existing list of todos
  }

  // Function to toggle the completion status of a todo item
  const toggleTodo = (id) => {
    // Mapping over the existing todos array and toggling the completion status of the todo item with the specified ID
    const updatedTodos = todos.map(todo =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    );
    setTodos(updatedTodos); // Updating the state with the updated todo list
  }

  // Rendering JSX (JavaScript XML) to represent the TodoPage component
  return (
    <div className="todo-page"> {/* Container div with class name "todo-page" */}
      <h1>To-Do List</h1> {/* Heading for the todo list */}
      <TodoForm addTodo={addTodo} /> {/* Rendering TodoForm component and passing addTodo function as prop */}
      <div className="todo-list"> {/* Container div for displaying todo items */}
        {todos.map(todo => (
          <TodoItem key={todo.id} todo={todo} toggleTodo={toggleTodo} />
        ))} {/* Mapping over the todo list and rendering TodoItem component for each todo item */}
      </div>
      <div className='todo-credits'> {/* Container div for displaying credits */}
        <a href='https://hashnode.com/@hugotav'>By Hugo Tavares</a> {/* Link to the author's profile */}
      </div>
    </div>
  );
}

export default TodoPage; // Exporting TodoPage component for use in other files
```

## Step 5: Styling the Application

Finally, let's style our application. Inside the `styles` folder, create a file named `TodoStyles.css` and add CSS styles for the components.

```css
/* TodoStyles.css - https://hashnode.com/@hugotav */
.todo-page {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #f4f4f4;
  border-radius: 8px;
}

.todo-page h1{
  text-align: center;
}

.todo-item {
  display: flex;
  align-items: center;
  margin-bottom: 0px;
}

.todo-item p {
  margin-left: 8px;
}

.todo-item input[type="checkbox"] {
  margin-right: 8px;
}

.completed {
  text-decoration: line-through;
  color: #888;
}

.completed input[type="checkbox"] {
  opacity: 0.5;
}

.todo-list {
  margin-top: 0px;
  margin-bottom: 0px;
}

.todo-credits {
  margin-top: 20px;
  align-items: center;
  text-align: center;
  font-size: smaller;
  font-weight: bold;
}

.todo-credits a {
  text-decoration: none;
}
```

## **Viewing Your Work 👀**

After following all the steps to create your Todo List with React, you'll be ready to view your work. To do this, the key command is `npm start`, which starts the development server and opens your React application in a web browser.

### **Running the Application**

Make sure you're in the directory of your project in the terminal. Then, execute the command:

```bash
npm start
```

This will start the development server and compile your React application. Once the compilation is complete, your default browser will automatically open, and you'll see your Todo List in action.

### **Accessing the React Page**

If the browser doesn't open automatically, you can manually access your application by typing the following address into the browser's address bar:

```http
http://localhost:3000
```

This will open the home page of your React application, where you can interact with your Todo List, add new tasks, mark tasks as completed, and more.

![View of To-Do List in browser](https://cdn.hashnode.com/res/hashnode/image/upload/v1715692778780/e86c3132-fad6-40b1-8b0b-353c8b59c055.png align="center")

### **Keeping the Server Running**

While you're working on your project, the development server will be running, and any changes you make to the files will automatically be reflected in the browser without needing to restart the server.

### **Shutting Down the Server**

When you're finished working on your application, you can shut down the development server by pressing `Ctrl + C` in the terminal where the server is running.

With this, you'll have full control over your React application and can view and test your work as you progress in developing your Todo List.

Now that you've learned how to view and access your React application, you're ready to create your own Todo List and explore all the potential that React has to offer!

## Conclusion ✅

Now that we've implemented our basic To-Do List with React and added the functionality to mark tasks as completed, the possibilities for expansion are endless. You can further enhance your application by adding features like task deletion, filtering tasks by completion status, or even integrating with a database to save tasks persistently.

This tutorial has provided you with a solid foundation to start creating your own applications with React. Whether you're building a simple to-do list or a complex web application, React offers the flexibility and power to bring your ideas to life. I hope you found this tutorial helpful, and I can't wait to see what you create next! 😉