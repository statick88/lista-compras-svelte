<script>
  let items = ['Manzanas', 'Bananas', 'Naranjas'];
  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, newItem];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }
</script>

<div class="container mt-5">
  <h1 class="mb-4">Shopping List</h1>

  <div class="input-group mb-3">
    <input type="text" class="form-control" bind:value={newItem} placeholder="Add item">
    <button class="btn btn-primary" on:click={addItem}>Add</button>
  </div>

  <ul class="list-group">
    {#each items as item, index}
      <li class="list-group-item d-flex justify-content-between align-items-center">
        {item}
        <button class="btn btn-danger" on:click={() => removeItem(index)}>Remove</button>
      </li>
    {/each}
  </ul>
</div>
