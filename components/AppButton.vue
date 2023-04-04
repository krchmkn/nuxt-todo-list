<template>
  <button
    class="button"
    type="button"
  >
    <slot />
  </button>
</template>

<style lang="scss" scoped>
.button {
  display: grid;
  place-content: center;
  place-items: center;
  border: 0;
  padding: 5px 10px;
  background: $orange;
  border-radius: 7px;
  text-transform: uppercase;
  color: #FFFFFF;
  font-size: 14px;
  line-height: 17px;
  transition: all $time;
  cursor: pointer;

  &:hover {
    background: $orange-dark;
  }

  &:active {
    transform: scale3d(0.95, 0.95, 0.95);
  }
}
</style>