<script>
  import { scale } from "svelte/transition";
  import TodoForm from "./components/TodoForm.svelte";
  import TodoItem from "./components/TodoItem.svelte";

  let todosData = [
    {
      id: 1,
      todo: "add todo from above 👆",
    },
    {
      id: 2,
      todo: "or click here to delete todo 👉",
    },
  ];

  let transitionName;

  const addTodoItem = (e) => {
    todosData = [...todosData, e.detail];
  };

  const handleDelete = (id) => {
    todosData = todosData.filter((todo) => todo.id !== id);
  };
</script>

<main>
  <div class="sticky">
    <TodoForm on:addTodo={addTodoItem} />
  </div>
  {#each todosData as todoItem (todoItem.id)}
    <div transition:scale>
      <TodoItem on:delete={() => handleDelete(todoItem.id)} item={todoItem} />
    </div>
  {/each}
</main>

<style>
  main {
    padding: 20px 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 15px;
  }

  .sticky {
    position: sticky;
    top: 0;
  }
</style>
