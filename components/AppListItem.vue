<template>
  <div
    class="list-item"
    :class="{'list-item--linethrough': selected}"
    @click="toggle"
    @mouseenter="hovered = true"
    @mouseleave="hovered = false"
  >
    <AppCheckbox
      :checked="selected"
      :hovered="hovered"
    />

    <div class="list-item__text">
      <div class="list-item__title">{{ data.title }}</div>
      <div class="list-item__subtitle">{{ data.subtitle }}</div>
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  data: ListItem
}>()

const emit = defineEmits<{
  (e: 'select', {}: SelectedListItem): void
}>()

const selected = ref(false)
const hovered = ref(false)

function toggle() {
  selected.value = !selected.value
  emit('select', { id: props.data.id, selected: selected.value });
}
</script>

<style lang="scss" scoped>
.list-item {
  display: grid;
  grid-template-columns: auto 1fr;
  place-items: center;
  gap: 15px;
  padding: 9px 15px;
  cursor: pointer;
  transition: color $time;
  width: 100%;

  &:hover {
    color: $orange
  }

  &--linethrough {
    color: $gray-light;

    &:hover {
      color: #fff;
    }
  }

  &--linethrough &__title,
  &--linethrough &__subtitle {
    text-decoration-line: line-through;
  }

  &__text {
    overflow: hidden;
    width: 100%;
  }

  &__subtitle {
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 15px;
    color: $gray-light;
    padding-top: 3px;
    overflow: hidden;
    white-space: nowrap;
    position: relative;

    &:after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      right: 0;
      background: linear-gradient(to right, transparent, $gray);
      width: 50px;
    }

    &:hover {
      color: $gray-light
    }
  }
}
</style>