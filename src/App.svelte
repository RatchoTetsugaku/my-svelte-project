<script>
  export let name, count;
  let loggedIn = false;

  // リアクティブ宣言 変数
  $: doubled = count * 2;

  // ステートメント
  $: console.log(`the count is ${count}`);

  // ステートメント(グループ)
  $: {
    console.log(`THE doubled IS ${doubled}`);
    let trippled = count * 3;
    console.log(`THE trippled IS ${trippled}`);
  }

  // ステートメント(コードブロック)
  $: if (count >= 10) {
    alert(`Don't count me out anymore!`);
    count = 9;
  }

  function handleClick() {
    count += 1;
  }

  function toggleStatus() {
    loggedIn = !loggedIn;
  }
</script>

<main>
  <h1>Hello {name}!</h1>
  <div class="hoge-class">
    {count} doubled is {doubled}
  </div>
  <p>Svelte apps.</p>

  <button on:click={handleClick}>
    Clicked {count}
    {count === 1 ? 'time' : 'times'}
  </button>

  <!-- {#if loggedIn}
    <button on:click={toggleStatus}> Log out </button>
  {/if}
  {#if !loggedIn}
    <button on:click={toggleStatus}> Log in </button>
  {/if} -->

  {#if loggedIn}
    <button on:click={toggleStatus}> Log out </button>
  {:else}
    <button on:click={toggleStatus}> Log in </button>
  {/if}
  <!-- #文字はblockの始まりを、
/文字はブロックの終わりを、
:はブロックが続けられることを表しています。 -->
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  .hoge-class {
    font-weight: bold;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
