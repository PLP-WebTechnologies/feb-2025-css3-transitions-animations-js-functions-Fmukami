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



<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>CSS3 & JavaScript Interactivity</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>

  <header>
    <h1>Welcome to the Animated Page</h1>
  </header>

  <main>
    <section>
      <label for="themeSelect">Choose Background Color:</label>
      <select id="themeSelect">
        <option value="white">White</option>
        <option value="lightblue">Light Blue</option>
        <option value="lavender">Lavender</option>
      </select>
      <button id="savePreference">Save Preference</button>
    </section>

    <section>
      <h2>Animated Image</h2>
      <img src="https://images.pexels.com/photos/207962/pexels-photo-207962.jpeg" alt="Forest" id="animatedImage" />
      <button id="animateBtn">Animate Image</button>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Animation & LocalStorage Demo</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>

/* General Styling */
body {
  font-family: 'Segoe UI', sans-serif;
  background-color: white;
  padding: 20px;
  transition: background-color 0.5s ease;
}

h1, h2 {
  text-align: center;
  margin-bottom: 20px;
}

button {
  padding: 10px 20px;
  margin-top: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #388e3c;
}

/* Image styling and animation */
#animatedImage {
  display: block;
  margin: 20px auto;
  max-width: 300px;
  border-radius: 10px;
  transition: transform 0.4s ease;
}

.animate-spin {
  animation: spin 1s linear forwards;
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

// Apply saved theme on page load
window.addEventListener('DOMContentLoaded', () => {
  const savedColor = localStorage.getItem('preferredColor');
  if (savedColor) {
    document.body.style.backgroundColor = savedColor;
    document.getElementById('themeSelect').value = savedColor;
  }
});

// Save preference and apply background color
document.getElementById('savePreference').addEventListener('click', () => {
  const color = document.getElementById('themeSelect').value;
  localStorage.setItem('preferredColor', color);
  document.body.style.backgroundColor = color;
});

// Animate image on button click
document.getElementById('animateBtn').addEventListener('click', () => {
  const img = document.getElementById('animatedImage');
  img.classList.remove('animate-spin'); // Reset
  void img.offsetWidth; // Trigger reflow
  img.classList.add('animate-spin');
});


