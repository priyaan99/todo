<script>
    import 'milligram';

    let todos = [
        {title: "First Todo", is_done: false},
        {title: "Second Todo", is_done: false},
    ];

    let num_of_todos = todos.length;

    let todo_name = '';
    let todo_done = false;

    function add_todo() {
        if (todo_name.length == 0) return; 

        let new_todo = {title: todo_name, is_done: todo_done};
        todos = [...todos, new_todo];

        todo_name = '';
        todo_done = false;
    }

    function delete_todo(index) {
        let todo = todos[index];
        todos = todos.filter((t) => t != todo);
    }

</script>

<body>

<div class="title">
  <h2>Todo App</h2>
</div>

<table>
  <thead>
    <tr>
      <th>Title</th>
      <th>Progress</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
  {#each todos as todo, i (i)}
    <tr>
      <td>{todo.title}</td>
      {#if todo.is_done}
        <td>Done</td>
      {:else}
        <td>undone</td>
      {/if}
      <td>
        <button on:click={() => delete_todo(i)}>Delete</button>
      </td>
    </tr>
  {/each}
  </tbody>
</table>

<div class="new_todo">

<h2>New Todo</h2>
<table>
  <tbody>
    <tr>
      <td><h3>Title</h3></td>
      <td>
        <input type="text" bind:value={todo_name}/>
      </td>
    </tr>
    <tr>
      <td><h3>Progress</h3></td>
      <td><input type="checkbox" bind:checked={todo_done}/></td>
    </tr>
  </tbody>
</table>

</div>

<button on:click={() => {add_todo()}}>Add todo</button>

</body>


<style>

body {
    padding: 1rem;
}

.title {
    display: flex;    
    align-items: center;
    justify-content: center;
}

.new_todo {
    padding-top: 2rem;
}

</style>
