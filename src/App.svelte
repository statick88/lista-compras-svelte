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

  function toggleItem(index) {
    items[index] = items[index].startsWith('~') ? items[index].slice(2) : '~' + items[index];
  }
</script>

<h1>Shopping List</h1>

<input class="btn-principal" type="text" bind:value={newItem} placeholder="Agregar item">
<button  on:click={addItem}>Add</button>

<ul class="lista">
  {#each items as item, index}
    <li style="{items[index].startsWith('~~') ? 'text-decoration: line-through;' : ''}">
      <label>
        <input type="checkbox" on:click={() => toggleItem(index)}> {items[index].startsWith('~~') ? items[index].slice(2) : items[index]}
      </label>
      <button class="botones" on:click={() => removeItem(index)}>Remove</button>
    </li>
  {/each}
</ul>