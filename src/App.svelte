<!-- app.svelte -->
<script>
  let items = ['Manzanas', 'Bananas', 'Naranjas'];
  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, { text: newItem, checked: false }];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }

  function toggleChecked(index) {
    items[index].checked = !items[index].checked;
  }
</script>

<div class="container">
  <h1>Shopping List</h1>

  <div id="shoppingList">
    <input type="text" bind:value={newItem} placeholder="Add item">
    <button on:click={addItem}>Add</button>
  </div>

  <ul>
    {#each items as { text, checked }, index}
      <li class:completed={checked}>
        <span>{text}</span>
        <button on:click={() => toggleChecked(index)}>Check</button>
        <button on:click={() => removeItem(index)}>Remove</button>
      </li>
    {/each}
  </ul>
</div>
