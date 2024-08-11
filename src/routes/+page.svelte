<script>
  let counter = $state(0);
</script>

<h1>Home Page on /</h1>
<section id="counter">
  <button onclick="{() => counter--}">➖</button>
  {#if counter < 10}
    <p>Count {counter}</p>
  {:else}
    <p>Finish</p>
  {/if}
  <button onclick="{() => counter++}">➕</button>
</section>
{#if counter < 10}
  <progress type="progress" value="{counter}" max="10"
    >{counter * 10}%</progress>
{:else}
  <button id="reset" onclick="{(counter = 0)}">Reset</button>
{/if}

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
  progress {
    display: block;
  }

  #reset {
    padding: 0.5rem 1rem;
    font-size: 1.5rem;
    background-color: lightgreen;
    border-radius: 10px;
    color: #333;
  }
</style>
