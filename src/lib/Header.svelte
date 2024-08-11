<script>
  import Nav from './Nav.svelte';
</script>

<h1>Titolo della Pagina</h1>
<Nav />

<style lang="scss">
  h1 {
    padding: 2rem 1rem;
    text-align: center;
    @media screen and (max-width: 430px) {
      padding: 0 0 1rem;
    }
  }
</style>
