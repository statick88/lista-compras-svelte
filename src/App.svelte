<script>
  let items = ['Manzanas', 'Bananas', 'Naranjas'];
  let newItem = '';
  let completedItems = new Array(items.length).fill(false);

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, newItem];
      completedItems = [...completedItems, false];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
    completedItems = completedItems.filter((_, i) => i !== index);
  }

  function toggleComplete(index) {
    completedItems[index] = !completedItems[index];
  }
</script>

<style>


  h1 {
    color: white;
  }

  input[type="text"] {
    padding: 10px;
    border: 1px solid #ddd;
    width: 200px;
  }

  button {
    padding: 10px 20px;
    background-color: #007BFF;
    color: white;
    border: none;
    margin-left: 10px;
    cursor: pointer;
  }

  button:hover {
    background-color: #0056b3;
  }

  ul {
    list-style-type: none;
    padding: 0;
    color : #333;
  }

  li {
    margin: 10px 0;
    background-color: #ddd;
    padding: 10px;
    border-radius: 5px;
  }

  .completed {
    text-decoration: line-through;
    background-color: #90EE90; /* Color de fondo para elementos completados */
  }

  .not-completed {
    background-color: #FFB6C1; /* Color de fondo para elementos no completados */
  }
</style>


<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<ul>
  {#each items as item, index}
    <li class:completed={completedItems[index]} class:not-completed={!completedItems[index]}>
      {item} 
      <button on:click={() => removeItem(index)}>Remove</button>
      <button on:click={() => toggleComplete(index)}>{completedItems[index] ? 'No Nompletado' : 'Completado'}</button>
    </li>
  {/each}
</ul>
