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


.my-button {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease; /* Smooth background color change */
}

.my-button:hover {
  background-color: #0056b3; /* Darker shade on hover */
  animation: pulse 1s infinite alternate; /* Apply the pulse animation */
}

@keyframes pulse {
  0% {
    transform: scale(1);
  }
  100% {
    transform: scale(1.05);
  }
}

function saveThemePreference(theme) {
  localStorage.setItem('preferredTheme', theme);
}

function getThemePreference() {
  return localStorage.getItem('preferredTheme') || 'light'; // Default to 'light' if nothing is stored
}

// Example of how you might use these functions
function setTheme(theme) {
  document.body.className = theme; // Apply the theme class to the body
  saveThemePreference(theme);     // Remember the preference
}

// On page load, apply the saved theme (if any)
document.addEventListener('DOMContentLoaded', () => {
  const savedTheme = getThemePreference();
  setTheme(savedTheme);
});

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-10px);
  }
  60% {
    transform: translateY(-5px);
  }
}

.bounce-animation {
  animation: bounce 0.5s ease-in-out;
}
const myButton = document.querySelector('.my-button');

myButton.addEventListener('click', () => {
  myButton.classList.add('bounce-animation');

  // Remove the class after the animation finishes to allow it to trigger again
  setTimeout(() => {
    myButton.classList.remove('bounce-animation');
  }, 500); // Matches the duration of the bounce animation
});

