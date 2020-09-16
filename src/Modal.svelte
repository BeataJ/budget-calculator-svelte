<script>
  import { blur, fade, fly } from 'svelte/transition';
</script>

<div class="modal-container" in:blur out:fade>
  <div class="modal-content">
    <slot />
  </div>
</div>
