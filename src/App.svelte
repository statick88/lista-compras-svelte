<script>
  let items = ['Manzanas', 'Bananas', 'Naranjas'];
  let newItem = '';
  let completedItems = [];

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, newItem];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }

  function completeItem(index) {
    const completedItem = items[index];
    completedItems = [...completedItems, completedItem];
    removeItem(index);
  }
</script>

<h1>Lista de compras</h1>

<input type="text" bind:value={newItem} placeholder="Add item">
<button on:click={addItem} class="btn btn-warning">Add</button>

<table class="shopping-list">
  <tbody>
    {#each items as item, index}
      <tr>
        <td>{item}</td>
        <td><button on:click={() => completeItem(index)} class="btn btn-success">Completado</button></td>
        <td><button on:click={() => removeItem(index)} class="btn btn-danger">Remove</button></td>
      </tr>
    {/each}
  </tbody>
</table>

<h1>Completados</h1>
<ul>
  {#each completedItems as completedItem}
    <li>{completedItem}</li>
  {/each}
</ul>