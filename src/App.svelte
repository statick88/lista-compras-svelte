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

<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<ul>
  {#each items as item, index}
    <li>{item} <button on:click={() => removeItem(index)}>Remove</button></li>
  {/each}
</ul>
