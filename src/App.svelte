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

<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<table>
  <thead>
    <tr>
      <th>Item</th>
      <th>Action</th>
      <th>Completed</th>
    </tr>
  </thead>
  <tbody>
    {#each items as item, index}
      <tr>
        <td style="text-decoration: {item.completed ? 'line-through' : 'none'}">{item.name}</td>
        <td><button on:click={() => removeItem(index)}>Remove</button></td>
        <td><button on:click={() => toggleCompleted(index)}>{item.completed ? 'No comprado' : 'Comprado'}</button></td>
      </tr>
    {/each}
  </tbody>
</table>
