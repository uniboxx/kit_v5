<script>
  import Nav from './Nav.svelte';
</script>

<h1>Get your cat</h1>
<Nav />

<style lang="scss">
  h1 {
    text-transform: capitalize;
    padding: 2rem 1rem;
    text-align: center;
    font-size: 3rem;
    color: #333;
    @media screen and (max-width: 430px) {
      padding: 0 0 1rem;
    }
  }
</style>
