<script>
  import japan from '$lib/images/DSC05830.jpg';
  import Nested from './nested/nested.svelte';
  import PackageInfo from './packageInfo.svelte';

  let name = 'Svelte';
  let string = 'this string contains some <strong>HTML!!!</strong>';
  let count = 0;
  let numbers = [1, 2, 3, 4];
  const pkg = {
    name: 'svelte',
    speed: 'blazing',
    version: 4,
    website: 'https://svelte.dev'
  };

  $: doubled = count * 2;// reactive declarations
  $: {
    console.log(`the count is ${count}`);
    console.log('this will also be in the log');
  }
  $: if(count >= 10) {
    alert('count is gettin high!');
    count = 0;
  }

  function increment() {
    count += 1;
  }
  function addNumber() {
    numbers.push(numbers.length + 1);
  }
  $: sum = numbers.reduce((total, currentNumber) => total + currentNumber, 0);
</script>

<h1>Welcome to SvelteKit {name.toUpperCase()}!</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
<Nested answer={42}/>
<Nested />
<p>{@html string}</p>
<p>{numbers.join(' + ')} = {sum}</p>
<button on:click={increment}>
  Clicked {count}
  {count === 1 ? 'time' : 'times'}
</button>
{#if count > 5}
  <p>{count} is greater than 5</p>
{:else if count < 3}
  <p>{count} is less than 3</p>
{:else}
  <p>{count} is between 0 and 5</p>    
{/if}
<button on:click={addNumber}>
  Add a number
</button>
<p>{count} doubled is {doubled}</p>

<PackageInfo {...pkg} />
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
