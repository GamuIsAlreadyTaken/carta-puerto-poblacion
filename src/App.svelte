<script lang="ts">
  import ListView from "./lib/ListView.svelte";

  import carta from "../static/carta.json";
import LangSelector from "./lib/LangSelector.svelte";
</script>

<div>
  <h1>El Puerto de la Población</h1>
  <LangSelector lang='es'/>
</div>

<ListView list={carta} />

<style>
  h1{
    text-align:  center;
    color: #a66
  }
</style>
