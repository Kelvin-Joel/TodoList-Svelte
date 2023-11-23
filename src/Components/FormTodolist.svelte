<script>
   export let initialState;
   export let AddTask;
   export let HidenComponent;
</script>

<form on:submit|preventDefault={()=>AddTask()}>
  <div class="form__header">
    <span class="form__btn-close" on:click={()=>HidenComponent()}>X</span>
  </div>
  <div class="form-control">
    <label for="txtname">Name :</label>
    <input autocomplete="off" type="text" name="name" placeholder="name" bind:value={initialState.name} />
  </div>
  <div class="form-control">
    <label for="txtname">Description :</label>
    <input
    bind:value={initialState.description}
      autocomplete="off"
      type="text"
      name="description"
      placeholder="description"
    />
  </div>
  <button class="form__btn">{initialState.id!== null ? "Edit" : "Save"}</button>
</form>

<style>
  form {
    box-shadow: 0 0 10px #333;
    width: 90%;
    border-radius: 5px;
  }
  .form__header {
    background-color: #2ecc71;
    padding: 1em 0;
    border-radius: 5px 5px 0 0;
    display: flex;
    justify-content: flex-end;
    padding-right: 1em;
  }
  .form__btn-close {
    height: 30px;
    width: 30px;
    background-color: #fff;
    color: red;
    border-radius: 50%;
    display: grid;
    place-items: center;
    font-weight: bold;
    font-size: 1.2em;
    cursor: pointer;
  }
  .form-control {
    padding: 1em;
  }
  .form-control label {
    color: #fff;
    font-size: 1.1em;
    display: block;
  }
  .form-control input {
    width: 100%;
    outline: none;
    border: none;
    border-radius: 5px;
    margin-bottom: 1em;
    background-color: #fafafafa;
    color: #111;
    font-family: sans-serif;
    font-size: 1em;
    padding: 0.8em;
  }
  .form__btn {
    background-color: #dc7633;
    color: #fff;
    margin-left: 1em;
  }
</style>
