<script>
  import { createEventDispatcher } from "svelte";
  import { v4 as uuidv4 } from "uuid";

  const dispatch = createEventDispatcher();

  let todoName;

  function handleSubmit() {
    dispatch("addTodo", { id: uuidv4(), todo: todoName });

    todoName = "";
  }
</script>

<form class="container" on:submit|preventDefault={handleSubmit}>
  <h1>Todo App</h1>
  <input type="text" bind:value={todoName} name="todo" placeholder="Add todo" />
  <button>Add</button>
</form>

<style>
  .container {
    width: 25rem;
    padding: 3rem 2rem;
    background-color: var(--color-three);
    display: flex;
    text-align: center;
    flex-direction: column;
    gap: 7px;
    border-radius: 15px;
    z-index: 10;
    box-shadow: -1px 6px 20px -1px rgba(0, 0, 0, 0.68);
    -webkit-box-shadow: -1px 6px 20px -1px rgba(0, 0, 0, 0.68);
    -moz-box-shadow: -1px 6px 20px -1px rgba(0, 0, 0, 0.68);
  }

  .container h1 {
    color: var(--bg-color);
  }
  .container input {
    padding: 5px;
    border: none;
    border-radius: 5px;
    outline: none;
  }

  .container button {
    padding: 5px;
    background-color: var(--color-one);
    color: var(--color-three);
    font-size: large;
    font-weight: bold;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
</style>
