<script>
  import Spinner from '../lib/Spinner.svelte';

  let counter = $state(0);

  const apiUrl = 'https://api.thecatapi.com/v1/images/search?size=small';
  const tumblr =
    'https://25.media.tumblr.com/tumblr_m1omvlbVGd1qze0hyo1_250.jpg';

  async function getCat() {
    try {
      const res = await fetch(apiUrl);
      if (!res.ok) return;
      const data = await res.json();
      const catUrl = data[0].url;
      if (catUrl === tumblr) return getCat();
      // console.log(data);
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
    onclick="{() => (counter -= 10)}"
    disabled="{counter === 0 || counter === 100}">➖</button>
  {#if counter < 100}
    <p>Click to get a cat {counter}%</p>
  {:else}
    <button id="restart" onclick="{() => (counter = 0)}">Restart</button>
  {/if}
  <button
    class="btn-counter"
    onclick="{() => (counter += 10)}"
    disabled="{counter === 100}">➕</button>
</section>

{#if counter < 100}
  <div id="progress-container">
    <div id="progress-bar" style="width:{counter}%"></div>
  </div>
{:else}
  {#await getCat()}
    <Spinner />
  {:then catUrl}
    <div>
      <img id="catImage" src="{catUrl}" alt="Nice cat" />
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
  #progress-container {
    border: 1px solid gray;
    width: 15rem;
    height: 1.5rem;
    line-height: 1.4;
    text-align: center;
    border-radius: 10px;
  }

  #progress-bar {
    background-color: lightgreen;
    height: 100%;
    transition: 0.3s;
    border-radius: 10px;
  }

  #restart {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background-color: lightgreen;
    border-radius: 10px;
    color: #333;
  }

  #catImage {
    max-width: 400px;
    width: 92svw;
    height: auto;
    border-radius: 10px;
    outline: 3px solid goldenrod;
    outline-offset: 5px;
    margin-top: 1rem;
  }
</style>
