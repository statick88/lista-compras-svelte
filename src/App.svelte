<script>
  let items = [
    { text: 'Manzanas', completed: false },
    { text: 'Bananas', completed: false },
    { text: 'Naranjas', completed: false },
  ];

  let newItem = '';

  function addItem() {
    if (newItem.trim() !== '') {
      items = [...items, { text: newItem, completed: false }];
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

<div class="container mt-5">
  <h1 class="mb-4">Shopping List</h1>

  <div class="input-group mb-3">
    <input type="text" class="form-control" bind:value={newItem} placeholder="Add item">
    <button class="btn btn-primary" on:click={addItem}>Add</button>
  </div>

  <ul class="list-group">
    {#each items as { text, completed }, index}
      <li class="list-group-item d-flex justify-content-between align-items-center">
        <span class={completed ? 'text-decoration-line-through' : ''}>{text}&nbsp;&nbsp;&nbsp;</span>


        <div>
          <button class="btn btn-success me-2" on:click={() => toggleCompleted(index)}>
            {completed ? 'incompleto' : 'completo'}
          </button>
          <button class="btn btn-danger" on:click={() => removeItem(index)}>Remove</button>
        </div>
      </li>
    {/each}
  </ul>
</div>

<style>
  .text-decoration-line-through {
    text-decoration: line-through;
    color: #6c757d; /* Color de texto gris para elementos completados */
  }
</style>
