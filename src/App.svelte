<script>
  let items = [
    { name: 'Manzanas', completed: false },
    { name: 'Bananas', completed: false },
    { name: 'Naranjas', completed: false }
  ];

  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, { name: newItem, completed: false }];
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
  .shopping-list {
    font-family: 'Roboto', sans-serif;
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
    max-width: 500px;
    margin: 20px auto;
  }

  h1 {
    text-align: center;
    color: #646cff;
    font-size: 32px;
    margin-bottom: 20px;
  }

  input[type="text"] {
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
    margin-right: 10px;
    width: calc(100% - 100px);
    font-size: 16px;
  }

  button {
    padding: 10px 20px;
    background-color: #646cff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
    font-size: 16px;
  }

  button:hover {
    background-color: #535bf2;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    margin-bottom: 10px;
    display: flex;
    align-items: center;
  }

  span {
    flex-grow: 1;
    font-size: 18px;
    color: #333;
  }

  .completed {
    text-decoration: line-through;
    color: #888;
  }

  .action-buttons button {
    margin-left: 10px;
    background-color: #f44336;
  }

  .action-buttons button:hover {
    background-color: #d32f2f;
  }
</style>

<h1>Shopping List</h1>

<div class="shopping-list">
  <input type="text" bind:value={newItem} placeholder="Add item">
  <button on:click={addItem}>Add</button>

  <ul>
    {#each items as item, index}
      <li>
        <span class="{item.completed ? 'completed' : ''}">{item.name}</span> 
        <div class="action-buttons">
          <button on:click={() => toggleCompleted(index)}>{item.completed ? 'Incompleto' : 'Completado'}</button>
          <button on:click={() => removeItem(index)}>Remove</button>
        </div>
      </li>
    {/each}
  </ul>
</div>
