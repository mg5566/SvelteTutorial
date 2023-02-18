<script>
  import Dividor from "../atoms/Dividor.svelte";
</script>

<div class="card-container">
  <slot name="title"></slot>
  <Dividor thick="medium" --track-color="black"/>
  <slot name="content"></slot>
</div>

<style>
  .card-container {
      border: 2px solid var(--color-theme-1);
      border-radius: 12px;
      padding: 1rem;
  }
</style>