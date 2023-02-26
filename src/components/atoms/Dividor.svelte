<script lang="ts">
  import type { Thick } from './Dividor.ts';

  export let thick: Thick = 'small';  // small, medium, large

  $: styledThick = () => {
    if (thick === 'small') {
      return '1px';
    } else if (thick === 'medium') {
      return '3px;'
    } else if (thick === 'large') {
      return '5px';
    }
    return '10px';
  }
</script>

<div class="dividor" style="{`--styled-thick: ${styledThick()};`}"></div>

<style>
  .dividor {
      padding: 0 1rem;
      /*background-color: var(--color-theme-2);*/
      background-color: var(--track-color);
      /*height: 2px;*/
      height: var(--styled-thick);
  }
</style>