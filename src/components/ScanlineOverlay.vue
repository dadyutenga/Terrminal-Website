<template>
  <div class="scanline" aria-hidden="true"></div>
</template>

<script setup></script>

<style scoped>
.scanline {
  position: fixed;
  inset: 0;
  pointer-events: none;
  background-image: repeating-linear-gradient(
      to bottom,
      rgba(255, 255, 255, 0.04) 0,
      rgba(255, 255, 255, 0.04) 1px,
      transparent 1px,
      transparent 3px
    ),
    radial-gradient(circle at 50% 0%, rgba(41, 240, 255, 0.12), transparent 60%);
  mix-blend-mode: overlay;
  opacity: 0.2;
  z-index: 1;
}
</style>
