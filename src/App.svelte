<script>
  let items = [
    { text: 'Manzanas', completed: false },
    { text: 'Bananas', completed: false },
    { text: 'Naranjas', completed: false }
  ];

  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, { text: newItem, completed: false }];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }

  function toggleCompleted(index) {
    items[index].completed = !items[index].completed;
  }
</script>

<style>
  body {
    font-family: 'Arial', sans-serif;
    background-color: #f4f4f4;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100vh;
    margin: 0;
  }

  h1 {
    color: #333;
    text-align: center;
  }

  input {
    padding: 10px;
    margin: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  button {
    padding: 10px;
    font-size: 16px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }

  button:hover {
    background-color: #45a049;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #fff;
    padding: 10px;
    margin: 5px 0;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  li button {
    background-color: #e53935;
    color: #fff;
    border: none;
    padding: 8px;
    border-radius: 4px;
    cursor: pointer;
  }

  li button:hover {
    background-color: #d32f2f;
  }

  li.completed {
    background-color: #e0f7fa;
    text-decoration: line-through;
  }
</style>

<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<ul>
  {#each items as { text, completed }, index}
    <li class:completed={completed}>
      <span>{text}</span>
      <div>
        <button on:click={() => toggleCompleted(index)}>
          {completed ? 'Mark Incomplete' : 'Mark Complete'}
        </button>
        <button on:click={() => removeItem(index)}>Remove</button>
      </div>
    </li>
  {/each}
</ul>
