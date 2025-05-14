# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Full JavaScript Demo Bundle</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 30px;
      background-color: #f4f4f4;
    }

    h2, h3 {
      color: #333;
    }

    form, .interactive-section, .tabs, .gallery {
      background-color: #fff;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0, 0, 0, 0.1);
    }

    label {
      display: block;
      margin-top: 10px;
    }

    input {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }

    .error {
      color: red;
      font-size: 0.85em;
    }

    button {
      margin-top: 15px;
      padding: 10px 15px;
      background-color: #007bff;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    button:hover {
      background-color: #0056b3;
    }

    #colorBox {
      width: 100px;
      height: 100px;
      margin-top: 10px;
      background-color: #ccc;
      transition: background-color 0.3s ease;
    }

    .tabs button {
      display: inline-block;
      margin-right: 5px;
      background-color: #eee;
    }

    .tab-content {
      display: none;
      margin-top: 15px;
    }

    .tab-content.active {
      display: block;
      animation: fadeIn 0.5s;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    .gallery img {
      width: 100px;
      height: auto;
      margin-right: 10px;
      cursor: pointer;
      transition: transform 0.3s ease;
    }

    .gallery img:hover {
      transform: scale(1.1);
    }
  </style>
</head>
<body>

  <h2>🌟 Full JavaScript Features Demo Page</h2>

  <!-- FORM WITH VALIDATION -->
  <form id="signupForm">
    <h3>Form Validation 📋</h3>
    <label>Name:</label>
    <input type="text" id="name" />
    <div class="error" id="nameError"></div>

    <label>Email:</label>
    <input type="text" id="email" />
    <div class="error" id="emailError"></div>

    <label>Password (min 8 characters):</label>
    <input type="password" id="password" />
    <div class="error" id="passwordError"></div>

    <button type="submit">Register</button>
  </form>

  <!-- INTERACTIVE BOX & EVENTS -->
  <div class="interactive-section">
    <h3>Event Handling 🎈</h3>
    <button id="eventBtn">Click me!</button>
    <div id="colorBox"></div>
    <p id="secret" style="margin-top:10px;"></p>
  </div>

  <!-- IMAGE GALLERY -->
  <div class="gallery">
    <h3>Image Gallery 🖼️</h3>
    <img src="https://via.placeholder.com/100" alt="Image 1" />
    <img src="https://via.placeholder.com/100" alt="Image 2" />
    <img src="https://via.placeholder.com/100" alt="Image 3" />
  </div>

  <!-- TABS / ACCORDION -->
  <div class="tabs">
    <h3>Tabs Interface 📁</h3>
    <button data-tab="tab1">Tab 1</button>
    <button data-tab="tab2">Tab 2</button>
    <div id="tab1" class="tab-content active">This is content for Tab 1.</div>
    <div id="tab2" class="tab-content">This is content for Tab 2.</div>
  </div>

  <script>
    // --- FORM VALIDATION ---
    const form = document.getElementById('signupForm');
    const nameInput = document.getElementById('name');
    const emailInput = document.getElementById('email');
    const passwordInput = document.getElementById('password');

    const nameError = document.getElementById('nameError');
    const emailError = document.getElementById('emailError');
    const passwordError = document.getElementById('passwordError');

    form.addEventListener('submit', function(e) {
      e.preventDefault();
      let valid = true;
      nameError.textContent = '';
      emailError.textContent = '';
      passwordError.textContent = '';

      if (nameInput.value.trim() === '') {
        nameError.textContent = 'Name is required.';
        valid = false;
      }
      const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;
      if (!emailPattern.test(emailInput.value.trim())) {
        emailError.textContent = 'Invalid email format.';
        valid = false;
      }
      if (passwordInput.value.length < 8) {
        passwordError.textContent = 'Password must be at least 8 characters.';
        valid = false;
      }

      if (valid) {
        alert('Registration successful!');
        form.reset();
      }
    });

    // Real-time feedback for password
    passwordInput.addEventListener('input', () => {
      passwordError.textContent = passwordInput.value.length < 8 ? 'Password too short.' : '';
    });

    // --- EVENT HANDLING ---
    const eventBtn = document.getElementById('eventBtn');
    const colorBox = document.getElementById('colorBox');
    const secret = document.getElementById('secret');

    eventBtn.addEventListener('click', () => {
      colorBox.style.backgroundColor = '#' + Math.floor(Math.random()*16777215).toString(16);
      eventBtn.textContent = 'Clicked!';
    });

    // Hover effect using JavaScript
    eventBtn.addEventListener('mouseover', () => {
      eventBtn.style.backgroundColor = 'green';
    });
    eventBtn.addEventListener('mouseout', () => {
      eventBtn.style.backgroundColor = '#007bff';
    });

    // Keypress detection
    document.addEventListener('keydown', (e) => {
      console.log('Key pressed:', e.key);
    });

    // Secret action: double click
    eventBtn.addEventListener('dblclick', () => {
      secret.textContent = '🎉 You discovered the secret double-click!';
    });

    // --- TABS FUNCTIONALITY ---
    const tabButtons = document.querySelectorAll('.tabs button');
    const tabContents = document.querySelectorAll('.tab-content');

    tabButtons.forEach(button => {
      button.addEventListener('click', () => {
        tabContents.forEach(content => content.classList.remove('active'));
        document.getElementById(button.getAttribute('data-tab')).classList.add('active');
      });
    });
  </script>
</body>
</html>

