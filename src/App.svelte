<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Shopping List</title>

  <!-- Include Bootstrap CSS -->
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
</head>


<div class="card mx-auto mt-5" style="max-width: 400px;">
  <div class="card-body">
    <h1 class="card-title text-center">Shopping List</h1>

    <input type="text" class="form-control mb-2" bind:value={newItem} placeholder="Add item">
    <button class="btn btn-primary btn-block" on:click={addItem}>Add</button>

    <table class="table mt-4">
      <tbody>
        {#each items as item, index}
          <tr>
            <td>{item}</td>
            <td>
              <button class="btn btn-danger" on:click={() => removeItem(index)}>Remove</button>
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="checkbox" id={`item-${index}`} name={`item-${index}`} value={item}>
                <label class="form-check-label" for={`item-${index}`}>Completado</label>
              </div>
            </td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>

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
 
