<p align="center">
  <img src="https://github.com/user-attachments/assets/1107ac66-99a7-4e46-a03f-8bb06bb205e5" alt="React Logo" width="300"/>
</p>

---

# 📅 Week 1: React Fundamentals + Frontend Setup

### Day 1: Introduction to React (1 hour)

### Overview

This session introduces the fundamentals of React and sets the foundation for frontend development using Vite. Learners will install required tools, create a project scaffold, and understand basic concepts like JSX and components.

# Topics Covered

- What is React?

- Advantages of using React

- What is Vite and why use it?

- Project initialization using Vite

- Introduction to JSX

### Creating and rendering components

### Lesson Content

### 1. What is React?

React is a JavaScript library for building user interfaces, especially single-page applications (SPAs). It lets developers create reusable components that manage their own state and efficiently update the UI when data changes.

### 2. Why Use React?

- Component-based architecture

- Virtual DOM for efficient rendering

- Strong ecosystem and community support

- Ideal for building modern web apps

### 3. What is Vite?

- Vite is a frontend build tool that offers fast development experience and instant server start. It serves source code via native ES modules and performs on-demand compilation.


### 4. Setting Up a React Project with Vite


Steps: 
1. Create a folder in Desktop or any location
2. Go to Visual Studio, open the folder
3. Open the terminal
Run the following command:

```bash
npm create vite@latest my-note-app --template react
```
![image](https://github.com/user-attachments/assets/a91de346-e860-4630-9f68-7a8aed1127eb)


Run the following command:
```bash
cd my-note-app
```
![image](https://github.com/user-attachments/assets/bdf6d98c-db1a-4356-9628-0cf271743707)


Run the following command:
```bash
npm install
```
![image](https://github.com/user-attachments/assets/cf09d158-a0a6-4d5b-8a89-603b482c1058)
<p align="center">The image shows that we have successfully installed react</p>






**Visit `http://localhost:5173` to see the project running.**
Run the following command:
```bash
npm run dev
```

![image](https://github.com/user-attachments/assets/fdd63305-8038-4ebe-8bf7-1b2d709be012)


### 5. Understanding JSX
JSX  is a syntax extension for JavaScript. It looks like HTML but compiles to  `React.createElement()` calls. JSX must return one root element and allows you to embed JavaScript expressions using curly braces {}.

Example:
```jsx
function Welcome() {
  return <h1>Hello, React!</h1>;
}
```


### 6. Creating and Rendering Components

![image](https://github.com/user-attachments/assets/b5ddd3e4-08da-4fea-8ced-73aa668e2378)

1. Inside the `src/components` directory, create a new file `Hello.jsx`.

![image](https://github.com/user-attachments/assets/0836d85f-cd8d-4da0-b5d0-6fc18e85972c)



```jsx
function Hello() {
  return <h2>Welcome to your first component!</h2>;
}

export default Hello;
```



**Explanation:**
### Part 1: Creating a Component
- You're making a new file called `Hello.jsx` inside a folder called `components`.
- Inside this file, you're creating a simple function called Hello that returns some text that says **"Welcome to your first component!"** with formatting to make it a medium-sized heading.
- At the bottom, you're making this function available for other files to use with **export default Hello.**

### Part 2: Using Your Component
- In your main `App.jsx` file, you're bringing in (importing) the `Hello` component you just created.
- Inside the `App function`, you're creating a layout that includes:

- A div container
- A large heading that says "My Note App"
- Your `Hello` component (shown as <Hello />)

This is the fundamental way React works - you build small, reusable pieces (components) and then combine them together in your main application.

2. In `App.jsx`, import and use the `Hello` component:
```jsx
import Hello from './components/Hello';

function App() {
  return (
    <div>
      <h1>My Note App</h1>
      <Hello />
    </div>
  );
}

export default App;
```



![image](https://github.com/user-attachments/assets/ecea340b-75ba-4cb5-9796-836144fbf61f)

![image](https://github.com/user-attachments/assets/e1a80bed-43e0-497a-a71f-3c5df1e6226d)

![image](https://github.com/user-attachments/assets/87128098-c7c2-46a9-9fb6-5a38b5dd0afc)
The page looks boring because no styling was added yet. It is just a simple page that displays a React component.


---
 ### Bonus: Styling a Component with Tailwind CSS
Once your project is running, let’s add Tailwind CSS to style a simple React card component.

### 1. Install Tailwind CSS
Run the following inside your project directory:

```bash
# Install Tailwind CSS
npm install -D tailwindcss @tailwindcss/vite
```

![image](https://github.com/user-attachments/assets/ef3c347a-ebc9-4f28-8eaa-65938016e519)



### 2. Configure Vite to Use Tailwind CSS:
Edit `vite.config.ts` (or `vite.config.js` if using JavaScript) file and add the Tailwind CSS plugin:
```jsx
// vite.config.ts
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [tailwindcss()],
})
```


![image](https://github.com/user-attachments/assets/874f96dc-4bbb-4fde-884c-943e4055861e)


### 4. Import Tailwind CSS in CSS File:
/* src/style.css */
```css
@import 'tailwindcss';
```

![image](https://github.com/user-attachments/assets/d8e1f4c6-a84b-40a1-9766-c97594346e04)




### 4. Create a Card Component
Create `Card.jsx` inside `src/components/`:

```jsx

import RivanBuilding from "../assets/rivan_building.png";


function Card() {
  return (
    <div className="max-w-sm mx-auto mt-5 p-6 bg-white rounded-xl shadow-md space-y-4">
      <img
        src={RivanBuilding} // path/to/your/image.jpg
        alt="Rivan Cyber Institute"
        className="w-full h-48 object-cover rounded-lg"
      />
      <h2 className="text-xl font-bold text-gray-900">
        Rivan Cyber Training Institute
      </h2>
      <p className="text-gray-700">
        #1 Best IT Certifications Training Center for Networking, Cybersecurity, and Beyond
      </p>
    </div>
  );
}

export default Card;

```

To insert an image, just drag the image in assets' folder
![image](https://github.com/user-attachments/assets/63a53537-ebf4-4f80-a3b7-6a9666d70ede)


![image](https://github.com/user-attachments/assets/c1243c7d-f600-4746-8ee9-9714fcfe4aa9)







In `App.jsx`, render it:
```jsx
import Card from './components/Card';

function App() {
  return (
    <div className="min-h-screen bg-gray-100 p-4">
      <h1 className="text-center text-2xl font-semibold mb-4">My First Web App</h1>
      <Card />
    </div>
  );
}

export default App;
```

---
### Remember: Always cd the react folder before running the server


Run the server:
```bash
npm run dev
```

---

![image](https://github.com/user-attachments/assets/2fecb881-dc2f-4af9-a491-0da7d9172ce2)





**Hands-on Exercise**

**Task:** Create a new component named `Info.jsx` that displays a short paragraph about React.

Render the Info component in `App.jsx` below the Card component.


---
**Summary**
By completing this session, you have a working React project scaffolded with Vite, understand JSX syntax, and be able to build and render simple components.


**Other references:**
---
https://react.dev/
https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Frameworks_libraries/React_getting_started
