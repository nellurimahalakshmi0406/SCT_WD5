# SCT_WD5
TO-DO WEB APP
<!DOCTYPE html>
<html>
<head>
    <title>Basic To-Do App</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f4f4f4;
            text-align: center;
            margin-top: 50px;
        }

        .container {
            background: white;
            width: 400px;
            margin: auto;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px gray;
        }

        input, button {
            padding: 8px;
            margin: 5px;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            background: #e3e3e3;
            margin: 5px 0;
            padding: 10px;
            border-radius: 5px;
        }

        .completed {
            text-decoration: line-through;
            background: #b2ffb2;
        }

        .task-info {
            font-size: 12px;
            color: gray;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>My To-Do List</h2>

    <input type="text" id="taskInput" placeholder="Enter task">
    <input type="datetime-local" id="taskDateTime">
    <button onclick="addTask()">Add</button>

    <ul id="taskList"></ul>
</div>

<script>
    function addTask() {
        let taskText = document.getElementById("taskInput").value;
        let taskDateTime = document.getElementById("taskDateTime").value;

        if (taskText === "") {
            alert("Please enter a task");
            return;
        }

        let li = document.createElement("li");

        let taskContent = document.createElement("span");
        taskContent.innerHTML = "<b>" + taskText + "</b>";

        let dateInfo = document.createElement("div");
        dateInfo.className = "task-info";
        dateInfo.innerText = taskDateTime ? "Due: " + taskDateTime : "";

        let completeBtn = document.createElement("button");
        completeBtn.innerText = "✔";
        completeBtn.onclick = function() {
            li.classList.toggle("completed");
        };

        let editBtn = document.createElement("button");
        editBtn.innerText = "Edit";
        editBtn.onclick = function() {
            let newTask = prompt("Edit task:", taskText);
            if (newTask !== null && newTask !== "") {
                taskText = newTask;
                taskContent.innerHTML = "<b>" + taskText + "</b>";
            }
        };

        let deleteBtn = document.createElement("button");
        deleteBtn.innerText = "Delete";
        deleteBtn.onclick = function() {
            li.remove();
        };

        li.appendChild(taskContent);
        li.appendChild(dateInfo);
        li.appendChild(completeBtn);
        li.appendChild(editBtn);
        li.appendChild(deleteBtn);

        document.getElementById("taskList").appendChild(li);

        document.getElementById("taskInput").value = "";
        document.getElementById("taskDateTime").value = "";
    }
</script>

</body>
</html>
