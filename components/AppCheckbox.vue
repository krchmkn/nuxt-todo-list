<template>
  <div
    class="checkbox"
    :class="{'checkbox--checked': checked, 'checkbox--hovered': hovered}"
  >
    <img v-cloak class="checkbox__icon"
      src="@/assets/img/icon-check.svg"
      alt=""
    />

    <label class="checkbox__input">
      List item checkbox
      <input type="checkbox" :checked="checked"/>
    </label>
  </div>
</template>

<script setup lang="ts">
defineProps<{
  checked: boolean,
  hovered?: boolean
}>()
</script>

<style lang="scss" scoped>
.checkbox {
  display: inline-flex;
  width: 20px;
  height: 20px;
  background: $gray-light;
  border-radius: 6px;
  padding: 4px;
  transition: background-color $time;

  &__input {
    display: none;
  }

  &__icon {
    display: none;
    width: 100%;
    height: auto;
    opacity: 0;
    transition: all $time;
  }

  &--hovered {
    background: rgba(255, 132, 105, 0.2);
  }

  &--checked {
    background: $orange;
    animation: pop-up $time;
  }

  &--checked .checkbox__icon {
    opacity: 1;
    display: inline-block;
  }
}

@keyframes pop-up {
  from { transform: scale3d(1, 1, 1) }
  50% { transform: scale3d(1.3, 1.3, 1.3) }
  to { transform: scale3d(1, 1, 1) }
}
</style>