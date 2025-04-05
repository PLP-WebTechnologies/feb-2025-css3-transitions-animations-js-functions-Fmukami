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

Happy Coding 

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Animations and LocalStorage</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            transition: background-color 0.5s ease; /* Smooth transition for theme changes */
        }
        body.dark-theme {
            background-color: #222;
            color: #eee;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
            transition: background-color 0.5s ease; /* Smooth transition for theme changes */
            max-width: 80%;
        }
        .container.dark-theme {
            background-color: #333;
            color: #fff;
            box-shadow: 0 4px 8px rgba(255, 255, 255, 0.1);
        }
        h1 {
            margin-bottom: 20px;
            transition: color 0.5s ease; /* Smooth transition for theme changes */
        }
        h1.dark-theme{
             color: #fff;
        }

        #myButton {
            padding: 12px 24px;
            font-size: 18px;
            background-color: #007bff;
            color: #fff;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition:
              background-color 0.3s ease,
              transform 0.2s ease; /* Added transform for scaling */
            margin-bottom: 20px;
        }

        #myButton:hover {
            background-color: #0056b3;
        }

        #myButton:active {
            background-color: #004080;
            transform: scale(0.95); /* Simulate button press */
        }

        .animated-image {
            width: 150px;
            height: auto;
            margin-top: 20px;
            border-radius: 8px;
            animation: fadeIn 2s ease, slideIn 1s ease-in-out forwards;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }
        @keyframes slideIn {
          from {
            transform: translateX(-100px);
          }
          to {
            transform: translateX(0);
          }
        }

        #themeSwitcher {
            padding: 10px 15px;
            font-size: 16px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            margin-top: 20px;
        }

        #themeSwitcher:hover {
            background-color: #45a049;
        }

        #themeSwitcher.dark-theme {
            background-color: #FFA500; /* A different color for dark theme */
        }

         #themeSwitcher.dark-theme:hover {
            background-color: #FF8C00;
        }

        .flash-warning {
            animation: flash 2s infinite;
            color: red;
        }

        @keyframes flash {
            0%, 50%, 100% { opacity: 1; }
            25%, 75% { opacity: 0; }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 id="mainTitle">Welcome!</h1>
        <button id="myButton">Click Me</button>
        <img src="https://placehold.co/150x80/EEE/31343C" alt="Placeholder Image" class="animated-image">
         <button id="themeSwitcher">Toggle Theme</button>
    </div>

    <script>
        const myButton = document.getElementById('myButton');
        const animatedImage = document.querySelector('.animated-image');
        const body = document.body;
        const container = document.querySelector('.container');
        const mainTitle = document.getElementById('mainTitle');
        const themeSwitcher = document.getElementById('themeSwitcher');

        // Function to add bounce animation
        function addBounceAnimation() {
            myButton.classList.add('bounce-animation');
            myButton.addEventListener('animationend', () => {
                myButton.classList.remove('bounce-animation');
            }, { once: true }); // Remove listener after it fires once
        }

        // Event listener for the button click
        myButton.addEventListener('click', addBounceAnimation);


        // Function to save theme preference to localStorage
        function saveThemePreference(theme) {
            localStorage.setItem('preferredTheme', theme);
        }

        // Function to get theme preference from localStorage
        function getThemePreference() {
            return localStorage.getItem('preferredTheme') || 'light'; // Default to 'light'
        }

        // Function to set the theme
        function setTheme(theme) {
            body.className = theme; // Apply theme to body
            container.className = `container ${theme}`; // Apply to container
            mainTitle.className = theme; // Apply to main title.
            themeSwitcher.className = themeSwitcher.className.replace(/(light|dark)-theme/g, '').trim() + ` ${theme}-theme`;

            saveThemePreference(theme); // Save to localStorage
        }

        // On page load, apply the saved theme
        document.addEventListener('DOMContentLoaded', () => {
            const savedTheme = getThemePreference();
            setTheme(savedTheme);
        });

       // Theme switcher button event listener
        themeSwitcher.addEventListener('click', () => {
            const currentTheme = body.className;
            const newTheme = currentTheme === 'dark-theme' ? 'light' : 'dark';
            setTheme(newTheme);
        });
    </script>
</body>
</html>


