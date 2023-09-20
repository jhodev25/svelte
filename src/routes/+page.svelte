<script>
  import japan from '$lib/images/DSC05830.jpg';
  import Nested from './nested/nested.svelte';

  let name = 'Svelte';
  let string = 'this string contains some <strong>HTML!!!</strong>';
  let count = 0;

  function increment() {
    count += 1;
  }
  
</script>

<h1>Welcome to SvelteKit {name.toUpperCase()}!</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<Nested />
<p>{@html string}</p>
<button on:click={increment}>
  Clicked {count}
  {count === 1 ? 'time' : 'times'}
</button>

<img src={japan} alt="japan skyscraper"/>

<style>
  p {
    color: goldenrod;
    /* font-family: 'Comic Sans MS', cursive; */
    font-size: 2em;
  }
  img {
    height: auto;
    width: 30%;
  }
</style>
