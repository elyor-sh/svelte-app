<script>
  import TodoCard from "./TodoCard.svelte";

  let value = "";
 let todos = [];

  function submitHandler(e) {
    e.preventDefault();
    let todo = {
      id: Date.now(),
      name: value,
    };
    todos = [...todos, todo];
    value = "";
  }
</script>

<form class="row jcsb" on:submit={submitHandler}>
  <div class="inputWrapper">
    <label for="todo">Add todo...</label>
    <input type="text" id="todo" bind:value />
  </div>
  <button type="submit"> Add </button>
</form>

{#if todos.length < 1}
    <p>No todos...</p>
{/if}

<TodoCard bind:todos={todos}/>

<style>
  form {
    margin-bottom: 30px;
  }

  input {
    outline: none;
    border: none;
    border-bottom: 1px solid #c4c4c4;
    width: 100%;
  }

  .inputWrapper {
    flex: 0 0 80%;
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
  }
</style>
