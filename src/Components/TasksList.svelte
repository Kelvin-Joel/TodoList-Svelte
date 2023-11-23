<script>
  export let tasksList;
  export let HidenComponent;
  export let tasksDelete;
  export let filldata;
  export let TaskComplete;
</script>

<div class="box__list-tasks">
  <button class="btn-new" on:click={()=>HidenComponent()}>New Task</button>
  {#each tasksList as values}
    <div class="box__tasks">
      <input type="checkbox"  class="checkbox" on:click={()=>TaskComplete(values.id)}/>
      <p class={`${values.state ? 'completed' : ''} box__text`} >{values.name} - {values.description}</p>
      <div class="box__buttons">
        <img src="IMG/EDIT.png" alt="edit" on:click={()=>filldata(values)}/>
        <img src="IMG/DELETE.png" alt="delete" on:click={()=>tasksDelete(values.id)}/>
      </div>
    </div>
  {/each}
</div>

<style>
    .box__list-tasks {
      outline: 1px solid #8e44ad;
      border-radius: 5px;
      padding: 1em;
      height: 450px;
      overflow-y: scroll;
    }
    .box__list-tasks::-webkit-scrollbar {
      width: .6em;
    }
  
    .box__list-tasks::-webkit-scrollbar-track {
      box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
    }
  
    .box__list-tasks::-webkit-scrollbar-thumb {
      background-color: #3498db;
      border-radius: 5px;
    }
    .box__tasks {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: #8e44ad;
      margin-bottom: 1em;
      border-radius: 5px;
      padding: 0.8em 1em;
    }
    .btn-new {
      margin-bottom: 1em;
      background-color: #3498db;
      color: #fff;
    }
    .box__text {
      margin: 0 1em;
      text-transform: uppercase;
      color: #fff;
    }
    .checkbox {
      padding: 0.8em;
      height: 20px;
      width: 20px;
      cursor: pointer;
    }
    img {
      height: 30px;
      width: 30px;
      cursor: pointer;
    }
    .completed {
      text-decoration: line-through;
    }
  </style>
