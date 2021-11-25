<script>
  import TodoCard from "./TodoCard.svelte";

  let value = "";
  let todos = JSON.parse(
    window.localStorage.getItem("todos") ||
      JSON.stringify([
        { id: 0, name: "Follow me on github for more...", completed: false },
      ])
  );

  function submitHandler(e) {
    e.preventDefault();
    if (!value.trim()) {
      alert("Enter something...");
      return;
    }
    let todo = {
      id: Date.now(),
      name: value,
      completed: false,
    };
    todos = [...todos, todo];
    window.localStorage.setItem("todos", JSON.stringify(todos));
    value = "";
  }

  const removeAllTodosHandler = (e) => {
    e.preventDefault();
    window.localStorage.clear();
    todos = [];
  };
</script>

<form class="row jcsb" on:submit={submitHandler}>
  <div class="inputWrapper">
    <label for="todo">Add todo...</label>
    <input type="text" id="todo" bind:value />
  </div>
  <button class="button" type="submit"> Add </button>
  <button class="button remove" on:click={removeAllTodosHandler}>
    Remove all todos
  </button>
</form>

{#if todos.length < 1}
  <p>No todos...</p>
{/if}

<TodoCard bind:todos />

<style>
  form {
    margin: 30px 0;
  }

  input {
    outline: none;
    border: none;
    border-bottom: 1px solid #c4c4c4;
    width: 100%;
  }

  .inputWrapper {
    flex: 0 0 60%;
  }

  button {
    flex: 0 0 15%;
    cursor: pointer;
    height: 50px;
    box-sizing: border-box;
    display: inline-block;
    background: #36ff40;
    color: #fff;
    border: none;
    outline: none;
    border-radius: 0;
  }

  .button.remove {
    background: #ff6549;
  }

  @media (max-width: 1100px) {
    .inputWrapper {
      flex: 0 0 50%;
    }
    .button {
      flex: 0 0 20%;
    }
  }
  @media (max-width: 768px) {
    .inputWrapper {
      flex: 0 0 48%;
    }
    .button {
      flex: 0 0 25%;
    }
  }
  @media (max-width: 576px) {
    form {
      flex-direction: column;
    }
    .button {
      padding: 10px 0px;
      text-align: center;
      display: inline-block;
      margin-top: 10px;
    }
  }
</style>
