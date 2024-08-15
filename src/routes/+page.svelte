<script>
  let counter = $state(0);

  const apiUrl = 'https://api.thecatapi.com/v1/images/search';

  async function getCat() {
    try {
      const res = await fetch(apiUrl);
      if (!res.ok) return;
      const data = await res.json();
      const catUrl = data[0].url;

      return catUrl;
    } catch (err) {
      console.error(err);
    }
  }
</script>

<h1>Home Page on /</h1>
<section id="counter">
  <button
    class="btn-counter"
    onclick="{() => counter--}"
    disabled="{counter === 10}">➖</button>
  {#if counter < 10}
    <p>Click to get a cat {counter}</p>
  {:else}
    <button id="restart" onclick="{() => (counter = 0)}">Restart</button>
  {/if}
  <button
    class="btn-counter"
    onclick="{() => counter++}"
    disabled="{counter === 10}">➕</button>
</section>

{#if counter < 10}
  <progress type="progress" value="{counter}" max="10"
    >{counter * 10}%</progress>
{:else}
  {#await getCat()}
    <p>Loading cat...</p>
  {:then catUrl}
    <div id="catImage">
      <img src="{catUrl}" alt="Nice cat" />
    </div>
  {:catch error}
    <p style="color:red;">{error.message}</p>
  {/await}
{/if}

<style lang="scss">
  #counter {
    display: flex;
    align-items: center;
    gap: 2rem;
    padding: 2rem;
    font-size: 2rem;
    & .btn-counter {
      font-size: inherit;
      &:disabled {
        cursor: not-allowed;
      }
    }
    & p {
      text-align: center;
    }
  }
  progress {
    display: block;
  }

  #restart {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background-color: lightgreen;
    border-radius: 10px;
    color: #333;
  }

  #catImage {
    width: auto;
    height: 300px;
    border-radius: 10px;
    outline: 3px solid goldenrod;
    outline-offset: 5px;
    margin-top: 3rem;
    @media screen and (max-width: 400px) {
      width: 92svw;
      height: auto;
    }
    & img {
      width: 100%;
      height: auto;
      border-radius: 10px;
    }
  }
</style>
