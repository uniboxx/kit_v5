<script>
  let counter = $state(0);
</script>

<h1>Home Page on /</h1>
<section id="counter">
  <button onclick="{() => counter--}">➖</button>
  <p>Count {counter}</p>
  <button onclick="{() => counter++}">➕</button>
</section>

<style lang="scss">
  #counter {
    display: flex;
    align-items: center;
    gap: 2rem;
    padding: 2rem;
    font-size: 2rem;
    & button {
      font-size: inherit;
    }
    & p {
      text-align: center;
    }
  }
</style>
