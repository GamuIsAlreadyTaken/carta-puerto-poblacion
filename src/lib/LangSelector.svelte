<script lang="ts">
  import { availableLangs } from "../stores/availableLangs.store";
  import { language } from "../stores/lang.store";
  export let lang: string;
  $: $language = lang;
</script>

{#each $availableLangs as posibleLang}
  <button class:selected={lang === posibleLang}
  on:click={()=>lang = posibleLang}>
    <img
      src="https://flagsapi.com/{posibleLang.toUpperCase()}/flat/64.png"
      alt={posibleLang}
    />
  </button>
{/each}

<style>
  button {
    padding: 0;
    border: none;
    background-color: transparent;
  }
  img {
    width: 25px;
    margin: 0 5px;
  }
  .selected {
    border-bottom: 2px solid white;
  }
</style>
