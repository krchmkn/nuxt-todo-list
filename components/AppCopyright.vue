<template>
  <div class="copyright">&copy; {{ year }}. Author Name</div>
</template>

<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<style lang="scss" scoped>
.copyright {
  padding: 30px 0;
  color: #414B62;
  display: grid;
  place-content: center;
  place-items: center;
  text-align: center;
}
</style>
