<script>
  let name = "world";
  setTimeout(() => {
    name = "Svelte";
  }, 2000);
</script>

<h1>Hello {name}</h1>

<style>
  h1 {
    color: purple;
  }
</style>
