<script lang="ts">
  import { language } from "../stores/lang.store";

  export let list;
  export let _importance = 2;
  const element = list.price ? `span` : `h${_importance}`;
  const cssclass = `title${_importance}`;

  const formatter = Intl.NumberFormat($language, {
    style: "currency",
    currency: "EUR",
  });
</script>

<div class={cssclass}>
  <svelte:element this={element}>{list[$language]}</svelte:element>
  {#if list.price}
    <svelte:element this={element} class="price">
      {typeof list.price == 'number'
        ? formatter.format(list.price)
        : list.price}
    </svelte:element>
  {/if}
</div>

{#if list.items}
  {#each list.items as item}
    <svelte:self list={item} _importance={_importance + 1} />
  {/each}
{/if}

<style>
  div {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
  .title2 *{
    text-align: center;
    width: 100%;
  }
  .title3 *{
    text-decoration: underline;
    margin-top: 20px;
    margin-bottom: 10px;
  }
  .title4{
    border-bottom: 1px solid #fff4;
  }
  .title4 * {
    margin: 0 0 0 10px;
    justify-self: center;
  }
  .price{
    border: none;
    position: relative;
    bottom: 0;
  }
</style>
