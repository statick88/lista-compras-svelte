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

  function toggleComplete(index) {
    items[index].completed = !items[index].completed;
  }
</script>

<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<ul class="list-group">
  {#each items as item, index}
    <li class="list-group-item">
      <div class="form-check">
        <input class="form-check-input" type="checkbox" bind:checked={item.completed} id={String(index)}>
        <label class="form-check-label {item.completed ? 'completed' : ''}" for={String(index)}>{item.name}</label>
        <button class="btn btn-danger" on:click={() => removeItem(index)}>Remove</button>
      </div>
    </li>
  {/each}
</ul>




<style>
  .completed {
    text-decoration: line-through;
  }
</style>
