<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css">

<script>
  let items = [
    { name: 'Manzanas', bought: true },
    { name: 'Bananas', bought: false },
    { name: 'Naranjas', bought: false }
  ];
  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, { name: newItem, bought: false }];
      newItem = '';
    }
  }

  function removeItem(index) {
    items = items.filter((_, i) => i !== index);
  }

  function toggleBought(index) {
    items[index].bought = !items[index].bought;
    items = [...items];
  }
</script>

<div class="container mt-5">
  <h1 class="mb-4">Lista de compras</h1>

  <div class="input-group mb-3">
    <input type="text" class="form-control" placeholder="Ingresa un producto" bind:value={newItem}>
    <button class="btn btn-primary" type="button" on:click={addItem}>Agregar</button>
  </div>

  <ul class="list-group">
    {#each items as item, index}
    <li class="list-group-item d-flex justify-content-between align-items-center" on:click={() => toggleBought(index)} style="cursor:pointer;text-decoration:{item.bought ? 'line-through' : 'none'};">
      {item.name}
      <div>
        <button class="btn btn-success me-2">{item.bought ? 'Deshacer' : 'Comprado'}</button>
        <button class="btn btn-danger" on:click={() => removeItem(index)}>Remove</button>
      </div>
    </li>
    {/each}
  </ul>
</div>

