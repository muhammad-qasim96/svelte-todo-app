<script>
  import { createEventDispatcher } from "svelte";

  export let item;

  const dispatch = createEventDispatcher();

  const handleDelete = () => {
    dispatch("delete");
  };
</script>

<div>
  <p>{item.todo}</p>
  <button on:click={handleDelete}>X</button>
</div>

<style>
  div {
    width: 25rem;
    padding: 2rem 1rem;
    display: flex;
    justify-content: space-between;
    background-color: var(--color-three);
    border-radius: 15px;
  }

  p {
    color: var(--bg-color);
    font-size: large;
    font-weight: 400;
    flex-grow: 1;
  }

  button {
    padding: 5px;
    background-color: transparent;
    border: none;
    font-size: 15px;
    font-weight: bold;
    cursor: pointer;
  }
</style>
