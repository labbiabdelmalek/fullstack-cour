// زر التجربة
const startBtn = document.getElementById("startBtn");
startBtn.addEventListener("click", (e) => {
  e.preventDefault();
  alert("مرحبا! JavaScript خدام 👌");
});

// ToDo Elements
const taskInput = document.getElementById("taskInput");
const addTaskBtn = document.getElementById("addTaskBtn");
const taskList = document.getElementById("taskList");

// Load tasks from localStorage
let tasks = [];
if (localStorage.getItem("tasks")) {
  tasks = JSON.parse(localStorage.getItem("tasks"));
  renderTasks();
}

addTaskBtn.addEventListener("click", () => {
  const taskText = taskInput.value.trim();

  if (!taskText) {
    alert("دخل شي مهمة");
    return;
  }

  tasks.push(taskText);
  taskInput.value = "";
  renderTasks();
});

function renderTasks() {
  taskList.innerHTML = "";

  tasks.forEach((task, index) => {
    const li = document.createElement("li");
    li.className = "list-group-item d-flex justify-content-between align-items-center";
    li.innerHTML = `
      <span>${task}</span>
      <button class="btn btn-sm btn-danger" onclick="deleteTask(${index})">حذف</button>
    `;
    taskList.appendChild(li);
  });

  localStorage.setItem("tasks", JSON.stringify(tasks));
}

function deleteTask(index) {
  tasks.splice(index, 1);
  renderTasks();
}

// Contact form (test)
const contactForm = document.getElementById("contactForm");
contactForm.addEventListener("submit", (e) => {
  e.preventDefault();
  alert("Merci! Formulaire reçu.");
});
