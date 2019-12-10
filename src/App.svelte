<script>
  import Todo from "./todo.svelte";

  let todos = [
    {
      id: 0,
      title: "Eggs",
      checked: false
    },
    {
      id: 1,
      title: "Milk",
      checked: false
    },
    {
      id: 2,
      title: "Butter",
      checked: false
    }
  ];
  let newTodoTitle = "";

  function checkTodo(id) {
    todos = todos.map(todo => {
      if (todo.id === id) {
        return {
          ...todo,
          checked: !todo.checked
        };
      }

      return todo;
    });
  }

  function addTodo(event) {
    event.preventDefault();

    if (newTodoTitle === "") {
      return;
    }

    todos = todos.concat({
      id: Math.random(),
      title: newTodoTitle,
      checked: false
    });

    newTodoTitle = "";
  }

  function removeTodo(id) {
    todos = todos.filter(todo => todo.id !== id);
  }

  export let name;
</script>

<style>
  :global(*) {
    box-sizing: border-box;
  }

  :global(body) {
    background-color: darksalmon;
    font-family: sans-serif;
    font-size: 16px;
    color: papayawhip;
  }

  .main {
    padding: 1em;
    max-width: 500px;
    margin: 0 auto;
  }

  .form {
    display: flex;
    flex-direction: row;
  }

  .input {
    flex-grow: 1;
    border: 0;
    border-radius: 4px 0 0 4px;
    padding: 1rem;
  }

  .submit {
    border: 0;
    background-color: papayawhip;
    color: darksalmon;
    border-radius: 0 4px 4px 0;
    padding: 0 1rem;
  }
</style>

<main class="main">
  <h1 class="title">{name}</h1>

  <form class="form" on:submit={addTodo}>
    <input class="input" type="text" bind:value={newTodoTitle} />
    <button class="submit" type="submit">Add</button>
  </form>

  {#each todos as todo}
    <Todo
      {todo}
      on:click={() => removeTodo(todo.id)}
      on:change={() => checkTodo(todo.id)} />
  {/each}

</main>
