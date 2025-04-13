# CSS3 Transitions, Animations, and Advanced JavaScript Functions

## Objectives

Create smooth CSS transitions and animations.
Use JavaScript functions for dynamic behavior.
Implement local storage for data persistence.

## Instructions
Add CSS animations to elements like buttons or images.

>[!NOTE]
> - Write a JavaScript function that:
> - Stores and retrieves user preferences using localStorage.
> - Implements an animation triggered by user actions.

## Tasks

Create a CSS animation.
Store data in localStorage.
Apply JavaScript to trigger animations.

Happy Coding! 💻✨

HTML Structure
Create a well-structured HTML5 document that includes semantic elements and links to external CSS and JavaScript files.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Interactive UI with Animations</title>
  <link rel="stylesheet" href="styles.css" />
</head>
<body>
  <header>
    <h1>Welcome to the Interactive Page</h1>
  </header>
  <main>
    <button id="animateBtn">Animate Box</button>
    <div id="box"></div>
    <section>
      <label for="themeSelect">Choose Theme:</label>
      <select id="themeSelect">
        <option value="light">Light</option>
        <option value="dark">Dark</option>
      </select>
    </section>
  </main>
  <script src="script.js"></script>
</body>
</html>

CSS Styling and Animations
Define styles for the elements and create animations using CSS transitions and keyframes.
/* styles.css */

/* Base styles */
body {
  font-family: Arial, sans-serif;
  transition: background-color 0.5s ease;
}

#box {
  width: 100px;
  height: 100px;
  background-color: coral;
  margin-top: 20px;
  transition: transform 0.5s ease;
}

/* Animation class */
.animate {
  transform: rotate(360deg);
}

/* Theme styles */
body.light {
  background-color: #ffffff;
  color: #000000;
}

body.dark {
  background-color: #2c2c2c;
  color: #ffffff;
}

JavaScript Functionality
Implement JavaScript functions to handle animations and manage user preferences using localStorage.

// script.js

document.addEventListener('DOMContentLoaded', () => {
  const box = document.getElementById('box');
  const animateBtn = document.getElementById('animateBtn');
  const themeSelect = document.getElementById('themeSelect');
  const body = document.body;

  // Load saved theme from localStorage
  const savedTheme = localStorage.getItem('theme') || 'light';
  body.classList.add(savedTheme);
  themeSelect.value = savedTheme;

  // Event listener for theme selection
  themeSelect.addEventListener('change', () => {
    const selectedTheme = themeSelect.value;
    body.classList.remove('light', 'dark');
    body.classList.add(selectedTheme);
    localStorage.setItem('theme', selectedTheme);
  });

  // Event listener for animation button
  animateBtn.addEventListener('click', () => {
    box.classList.add('animate');
    // Remove the class after animation completes to allow re-triggering
    setTimeout(() => {
      box.classList.remove('animate');
    }, 500); // Duration should match the CSS transition duration
  });
});

