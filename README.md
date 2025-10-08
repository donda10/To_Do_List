# Ex03 To-Do List using JavaScript
## Date: 8/9/2025

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My To-Do App</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');

    body {
      font-family: 'Poppins', sans-serif;
      background: linear-gradient(135deg, #74ABE2, #5563DE);
      display: flex;
      justify-content: center;
      align-items: flex-start;
      min-height: 100vh;
      padding-top: 60px;
      color: #333;
    }

    .container {
      background: #fff;
      width: 400px;
      border-radius: 15px;
      box-shadow: 0 5px 25px rgba(0,0,0,0.2);
      padding: 25px 20px;
    }

    h2 {
      text-align: center;
      color: #222;
      margin-bottom: 20px;
    }

    .input-area {
      display: flex;
      gap: 10px;
      margin-bottom: 20px;
    }

    input {
      flex: 1;
      padding: 10px;
      border: 2px solid #ddd;
      border-radius: 8px;
      font-size: 14px;
      transition: border 0.2s;
    }

    input:focus {
      outline: none;
      border-color: #5563DE;
    }

    button {
      padding: 10px 14px;
      border: none;
      background-color: #5563DE;
      color: white;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
    }

    button:hover {
      background-color: #3845b9;
    }

    ul {
      list-style: none;
      padding: 0;
    }

    li {
      background-color: #f2f3ff;
      padding: 10px;
      margin-bottom: 10px;
      border-radius: 8px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: all 0.3s ease;
    }

    li:hover {
      transform: scale(1.02);
      background-color: #e8eaff;
    }

    li.done {
      text-decoration: line-through;
      color: gray;
      background-color: #dcdcdc;
    }

    .actions button {
      background: none;
      border: none;
      cursor: pointer;
      font-size: 16px;
      margin-left: 6px;
      color: #5563DE;
    }

    .actions button:hover {
      color: #3845b9;
    }

    .footer {
      text-align: center;
      font-size: 13px;
      color: #777;
      margin-top: 15px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h2>📝 My To-Do List</h2>

    <div class="input-area">
      <input type="text" id="taskInput" placeholder="Enter a new task...">
      <button id="addBtn">Add</button>
    </div>

    <ul id="taskList"></ul>

   
  </div>

  <script>
    let addBtn = document.getElementById("addBtn");
    let taskInput = document.getElementById("taskInput");
    let taskList = document.getElementById("taskList");

    let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

    function showTasks() {
      taskList.innerHTML = "";
      tasks.forEach((task, i) => {
        let li = document.createElement("li");
        li.className = task.done ? "done" : "";
        li.innerHTML = `
          <span onclick="toggleTask(${i})">${task.name}</span>
          <div class="actions">
            <button onclick="editTask(${i})">✏️</button>
            <button onclick="deleteTask(${i})">🗑️</button>
          </div>
        `;
        taskList.appendChild(li);
      });
    }

    function addTask() {
      let text = taskInput.value.trim();
      if (text === "") {
        alert("Please enter a task!");
        return;
      }
      tasks.push({ name: text, done: false });
      taskInput.value = "";
      saveTasks();
      showTasks();
    }

    function toggleTask(index) {
      tasks[index].done = !tasks[index].done;
      saveTasks();
      showTasks();
    }

    function deleteTask(index) {
      tasks.splice(index, 1);
      saveTasks();
      showTasks();
    }

    function editTask(index) {
      let newName = prompt("Edit your task:", tasks[index].name);
      if (newName && newName.trim() !== "") {
        tasks[index].name = newName.trim();
        saveTasks();
        showTasks();
      }
    }

    function saveTasks() {
      localStorage.setItem("tasks", JSON.stringify(tasks));
    }

    addBtn.addEventListener("click", addTask);
    taskInput.addEventListener("keypress", function(e) {
      if (e.key === "Enter") addTask();
    });

    showTasks();
  </script>
</body>
</html>


```

## OUTPUT


<img width="1919" height="1032" alt="Screenshot 2025-10-08 100625" src="https://github.com/user-attachments/assets/bcdf7b97-d21a-41d2-ac00-e30f33558677" />




## RESULT
The program for creating To-do list using JavaScript is executed successfully.
