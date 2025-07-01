<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Intermediate HTML, CSS, and JS Project</title>
  <style>
   @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

body {
  margin: 0;
  font-family: 'Roboto', Arial, sans-serif;
  background: linear-gradient(135deg, #e0f2f1, #b2dfdb);
  color: #2c3e50;
}

header, footer {
  background-color: #00796b;
  color: #e0f2f1;
  text-align: center;
  padding: 1.2em 1em;
  box-shadow: 0 2px 8px rgba(0,0,0,0.15);
  font-weight: 700;
  letter-spacing: 1.2px;
}

main {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 25px;
  padding: 30px 40px;
  max-width: 900px;
  margin: 0 auto;
}

nav {
  display: flex;
  flex-direction: column;
  gap: 12px;
  background: #ffffffdd;
  padding: 25px 20px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
}

nav a {
  text-decoration: none;
  color: #00796b;
  font-weight: 700;
  padding: 12px 0;
  border: 2px solid transparent;
  border-radius: 8px;
  text-align: center;
  transition: all 0.3s ease;
  letter-spacing: 0.8px;
}

nav a:hover, nav a:focus {
  background: #00796b;
  color: #e0f2f1;
  border-color: #004d40;
  box-shadow: 0 4px 8px rgba(0,121,107,0.3);
}

section {
  background: #ffffffdd;
  padding: 30px 25px;
  border-radius: 12px;
  box-shadow: 0 6px 20px rgba(0,0,0,0.07);
}

h2 {
  color: #004d40;
  margin-bottom: 20px;
  font-weight: 700;
  letter-spacing: 0.8px;
}

form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

input, button {
  padding: 14px 18px;
  font-size: 16px;
  border-radius: 10px;
  border: 1.8px solid #b2dfdb;
  transition: all 0.3s ease;
  font-family: 'Roboto', Arial, sans-serif;
}

input:focus {
  outline: none;
  border-color: #00796b;
  box-shadow: 0 0 8px #00796b;
}

button {
  background-color: #00796b;
  color: white;
  border: none;
  cursor: pointer;
  font-weight: 700;
  letter-spacing: 1px;
  box-shadow: 0 4px 10px rgba(0,121,107,0.3);
}

button:hover, button:focus {
  background-color: #004d40;
  box-shadow: 0 6px 15px rgba(0,77,64,0.5);
  outline: none;
}

#form-message {
  font-weight: 600;
  margin-top: 12px;
  min-height: 20px;
}

#todo-input {
  border: 1.8px solid #b2dfdb;
  width: 100%;
  box-sizing: border-box;
}

#add-todo-btn {
  margin-top: 10px;
  width: 100%;
}

#todo-list {
  list-style-type: none;
  padding: 0;
  margin-top: 20px;
}

#todo-list li {
  padding: 12px 18px;
  background: #b2dfdb;
  margin: 8px 0;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  color: #004d40;
  box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  transition: background 0.3s ease;
}

#todo-list li:hover {
  background: #80cbc4;
  color: #00332a;
}

#todo-list li button {
  background: #d32f2f;
  border: none;
  color: white;
  padding: 6px 14px;
  cursor: pointer;
  border-radius: 8px;
  font-weight: 700;
  box-shadow: 0 3px 8px rgba(211,47,47,0.5);
  transition: background 0.3s ease;
}

#todo-list li button:hover {
  background: #9a0007;
}

@media (max-width: 768px) {
  main {
    grid-template-columns: 1fr;
    padding: 20px 15px;
  }

  nav {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
  }

  nav a {
    flex: 1 1 45%;
    margin-bottom: 12px;
  }

  #add-todo-btn {
    width: auto;
  }
}
  </style>
</head>
<body>

  <header>
    <h1>Intermediate HTML, CSS, and JS</h1>
  </header>

  <main>
    <nav>
      <a href="#contact-form">Contact Form</a>
      <a href="#todo-section">To-Do List</a>
    </nav>

    <section id="content">
      <section id="contact-form">
        <h2>Contact Form</h2>
        <form id="myForm">
          <input type="text" id="name" placeholder="Your Name" required />
          <input type="email" id="email" placeholder="Your Email" required />
          <button type="submit">Submit</button>
        </form>
        <p id="form-message"></p>
      </section>

      <section id="todo-section">
        <h2>To-Do List</h2>
        <input type="text" id="todo-input" placeholder="Add a new task..." />
        <button id="add-todo-btn">Add Task</button>
        <ul id="todo-list"></ul>
      </section>
    </section>
  </main>

  <footer>
    <p>&copy; 2025 Intermediate Web Project</p>
  </footer>

  <script>
    // JS Form Validation
    document.getElementById("myForm").addEventListener("submit", function(e) {
      e.preventDefault();
      const name = document.getElementById("name").value.trim();
      const email = document.getElementById("email").value.trim();
      const messageEl = document.getElementById("form-message");

      const emailPattern = /^[^ ]+@[^ ]+\.[a-z]{2,3}$/;

      if (name === "" || email === "") {
        messageEl.textContent = "All fields are required.";
        messageEl.style.color = "red";
        return;
      }

      if (!emailPattern.test(email)) {
        messageEl.textContent = "Please enter a valid email address.";
        messageEl.style.color = "red";
        return;
      }

      messageEl.textContent = "Form submitted successfully!";
      messageEl.style.color = "green";
      this.reset();
    });

    // Dynamic To-Do List
    document.getElementById("add-todo-btn").addEventListener("click", function() {
      const input = document.getElementById("todo-input");
      const text = input.value.trim();

      if (text === "") return;

      const li = document.createElement("li");
      li.textContent = text;

      const deleteBtn = document.createElement("button");
      deleteBtn.textContent = "Delete";
      deleteBtn.addEventListener("click", () => {
        li.remove();
      });

      li.appendChild(deleteBtn);
      document.getElementById("todo-list").appendChild(li);
      input.value = "";
    });
  </script>
</body>
</html>
