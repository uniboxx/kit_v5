<script>
  import '../app.scss';
  import Header from '../lib/Header.svelte';
  import Footer from '../lib/Footer.svelte';
</script>

<div id="container">
  <header id="header">
    <Header />
  </header>
  <main id="main">
    <slot />
  </main>
  <Footer />
</div>

<style lang="scss">
  #container {
    min-height: 100svh;
    display: grid;
    grid-template-rows: min-content 1fr min-content;
    padding: 1rem 0.5rem;
  }

  #main {
    display: flex;
    flex-direction: column;
  }
</style>
