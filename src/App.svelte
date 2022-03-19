<script>
  import { todos } from "~/store";
  import CreateToDo from "~/components/CreateToDo";
  import Todo from "~/components/Todo";

  const storagesTodos = localStorage.getItem('todos')
  if (storagesTodos) {
    $todos = JSON.parse(storagesTodos)
  }
</script>

<div class="container">
  <CreateToDo />
  <div class="todos">
    {#each $todos as todo (todo.id)}
      <Todo {todo} />
    {/each}
  </div>
</div>

<style lang="scss">
  .todos {
    padding: 20px 0;
  }
</style>
