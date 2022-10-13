
/* We create the array where the task information will be stored*/
var task_array = []

/* Function to create and build the list that will contin all the information that we want to display*/
function create_list() {
  var ul_element = document.querySelector("#all_tasks");

  /*Remove any present child elements from ul*/
  while (ul_element.firstChild) {
    ul_element.removeChild(ul_element.firstChild);
  }

  /* Insert Elements from task_array*/
  for (var i = 0; i < task_array.length; i++) {
    var li = document.createElement("li"); /* We create the list Element*/
    var checkbox = document.createElement("INPUT"); /* We create the Checkbox for list element*/

    /* Checkbocx in to mark the task as completed */
    checkbox.setAttribute("type", "checkbox");
    checkbox.onclick = markComplete; /* When clicking the checkbox, we call the markComplete function*/
    /* If the status of the new task added is completed, then we mark it as completed when we display it */
    if (task_array[i].status === "completed") {
      li.classList.add("completed");
      checkbox.checked = true;
    }

    /* Depending on the priority level of the new task added,
      we display the task in a different color format*/
    if (task_array[i].priority === "high") {
      li.style.color = "red";
    }
    else if(task_array[i].priority === "medium") {
      li.style.color = "orange";
    }
    else {
      li.style.color = "black";
    }

    /* Insert title and set attibutes previously collected*/
    li.innerHTML = task_array[i].title;
    li.insertBefore(checkbox, li.firstChild);
    li.setAttribute("id", task_array[i].title)

    /* We create the remove task button */
    var button = document.createElement("button");
    button.classList.add("remove_task");
    button.onclick = RemoveTask; /* Call the RemoveTask function when we clik on the button*/
    button.innerText = "✖";

    /* Append that task in an array as well as append the task-list in the HTML */
    li.appendChild(button);
    ul_element.appendChild(li);
  }
}


/*Function to add task in the array and then make an undordered list from that */
document.querySelector("#add_task").addEventListener("click", function(e) {

  /* Create the variable sthat we will add our array where the information collected in the form wil be stored */
  var title = document.querySelector("#title").value; /* Task title */
  var priority = document.querySelector("form select").value; /* Task priority */
  if (document.querySelector("#pending").checked) { /* If statement to set the task status */
    var status = "pending";
  }
  else {
    var status = "completed";
  }

  /* Add task in the array*/
  task_array.push({
    title: title,
    priority: priority,
    status: status
  })

  /* Create the unordered list using the information stored in the array */
  create_list();
  e.preventDefault();
})


/* Function to remove element from the tasks list */
function RemoveTask(e) {
  var id = e.target.parentElement.id;
  /* Remove element from the array which when rendered again removes item from the list */
  task_array = task_array.filter(data => data.title != id);
  create_list();
  e.preventDefault();
}

/* Function to mark a task as completed */
function markComplete(e) {
  var id = e.target.parentElement.id;
  task_array = task_array.map(x => {
    if (x.title === id) x.status = "completed";
    return x;
  })
  create_list();
}

/* We call the create_list function to run our code */
create_list();
