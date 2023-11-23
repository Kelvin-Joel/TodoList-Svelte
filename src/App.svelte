<script>
  import FormTodolist from "./Components/FormTodolist.svelte";
  import TasksList from "./Components/TasksList.svelte";

  let initialState = {
    id: null,
    name: "",
    description: "",
    state: false,
  };
  let showComponent = false;
  let tasksList = JSON.parse(localStorage.getItem("tasks")) || [];
  $: localStorage.setItem("tasks", JSON.stringify(tasksList));

  console.log(tasksList);

  const AddTask = () => {
    if (initialState.name === "") {
      return alert("Error Campos Vacios!!");
    }

    if (initialState.id !== null) {
      tasksList = tasksList.map((task) =>
        task.id === initialState.id ? initialState : task
      );
    } else {
      initialState.id = Date.now();
      tasksList = [...tasksList, initialState];
      console.log(tasksList);
      
    }
    HidenComponent();
    initialState = {
      id: null,
      name: "",
      description: "",
      state: false,
    };
  };

  const tasksDelete = (idtask) => {
    tasksList = tasksList.filter((task) => task.id !== idtask);
  };

  const filldata = (task) => {
    initialState = task;
    HidenComponent();
  };

  const HidenComponent = () => {
    showComponent = !showComponent;
  };

  const TaskComplete = (idtask) =>{
    tasksList = tasksList.map(task=>task.id === idtask ? {...task,state:!task.state} : task)
  }
</script>

{#if showComponent}
  <FormTodolist {initialState} {AddTask} {HidenComponent} />
{:else}
  <TasksList {tasksList} {HidenComponent} {tasksDelete} {filldata} {TaskComplete}/>
{/if}
