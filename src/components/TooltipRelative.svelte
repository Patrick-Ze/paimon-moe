<script>
  export let title = '';
  let isHovered = false;
  let x;
  let y;
  let ref;

  function mouseOver(event) {
    isHovered = true;
    const pos = ref.getBoundingClientRect();
    x = pos.x;
    y = pos.y + 30;
  }
  function mouseLeave() {
    isHovered = false;
  }
</script>

<span on:mouseover={mouseOver} on:mouseleave={mouseLeave} bind:this={ref}>
  <slot />
</span>

{#if isHovered}
  <div style="top: {y}px; left: {x}px;" class="tooltip">{title}</div>
{/if}

<style>
  .tooltip {
    @apply p-2 fixed rounded-xl bg-gray-400 border border-gray-800;
    @apply text-sm text-background z-10;
  }
</style>
