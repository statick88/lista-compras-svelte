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

  function markCompleted(index) {
    items[index].completed = true;
  }
</script>

<h1>Shopping List</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem}>Add</button>

<ul>
  {#each items as { name, completed }, index}
    <li>
      {#if !completed}
        {name} <button on:click={() => markCompleted(index)}>Mark as Completed</button>
      {:else}
        <s>{name}</s> (Completed)
        <button on:click={() => removeItem(index)}>Remove</button>
      {/if}
    </li>
  {/each}
</ul>