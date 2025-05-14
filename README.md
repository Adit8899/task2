<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Task 2 - Web Development Internship</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      margin: 0;
      background: #f4f4f4;
      color: #333;
    }

    header, footer {
      background: #333;
      color: #fff;
      padding: 10px;
      text-align: center;
    }

    .container {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      padding: 20px;
    }

    section {
      background: white;
      padding: 20px;
      border-radius: 10px;
    }

    img {
      width: 100%;
      border-radius: 10px;
    }

    form input, form textarea {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
    }

    form button {
      padding: 10px 20px;
      background: #333;
      color: white;
      border: none;
      cursor: pointer;
    }

    .error {
      color: red;
    }

    .todo-section input {
      padding: 10px;
      width: 70%;
    }

    .todo-section button {
      padding: 10px;
      background: green;
      color: white;
      border: none;
    }

    #taskList {
      list-style-type: none;
      padding: 0;
    }

    #taskList li {
      margin: 10px 0;
      padding: 10px;
      background: #eee;
      display: flex;
      justify-content: space-between;
    }

    @media screen and (max-width: 768px) {
      .container {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Welcome to My Internship Task 2</h1>
  </header>

  <main class="container">
    <!-- Image Section -->
    <section class="image-section">
      <img src="https://source.unsplash.com/400x250/?technology" alt="Tech Image">
    </section>

    <!-- Contact Form -->
    <section class="form-section">
      <h2>Contact Us</h2>
      <form id="contactForm">
        <input type="text" id="name" placeholder="Your Name" required />
        <input type="email" id="email" placeholder="Your Email" required />
        <textarea id="message" placeholder="Your Message" required></textarea>
        <button type="submit">Submit</button>
        <p id="formError" class="error"></p>
      </form>
    </section>

    <!-- To-Do List -->
    <section class="todo-section">
      <h2>My To-Do List</h2>
      <input type="text" id="taskInput" placeholder="Add a new task" />
      <button onclick="addTask()">Add Task</button>
      <ul id="taskList"></ul>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 My Internship Task</p>
  </footer>

  <script>
    // Form validation
    document.getElementById("contactForm").addEventListener("submit", function (e) {
      e.preventDefault();

      let name = document.getElementById("name").value.trim();
      let email = document.getElementById("email").value.trim();
      let message = document.getElementById("message").value.trim();
      let error = document.getElementById("formError");

      const emailRegex = /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/;

      if (!name || !email || !message) {
        error.textContent = "All fields are required.";
      } else if (!emailRegex.test(email)) {
        error.textContent = "Please enter a valid email.";
      } else {
        error.textContent = "";
        alert("Form submitted successfully!");
        document.getElementById("contactForm").reset();
      }
    });

    // To-Do List
    function addTask() {
      const input = document.getElementById("taskInput");
      const task = input.value.trim();

      if (task !== "") {
        const li = document.createElement("li");
        li.textContent = task;

        const btn = document.createElement("button");
        btn.textContent = "Delete";
        btn.style.marginLeft = "10px";
        btn.onclick = () => li.remove();

        li.appendChild(btn);
        document.getElementById("taskList").appendChild(li);

        input.value = "";
      }
    }
  </script>
</body>
</html>
