<template>
  <ul ref="listRef" class="list">
    <li
      v-for="item in list"
      :key="item.id"
      class="list-item"
    >
      <AppListItem
        :data="item"
        @select="onSelect"
      />
    </li>
  </ul>
</template>

<script setup lang="ts">
const props = defineProps<{
  list: Array<ListItem>
}>()

function onSelect(payload: SelectedListItem) {
  console.log("onSelect" , payload)
}

const listRef = ref<HTMLElement>()
function scrollBottom() {
  if (listRef.value) {
    listRef.value.scrollTop = listRef.value.scrollHeight
  }
}

watch(props.list, scrollBottom, { flush: 'post' });
</script>

<style lang="scss" scoped>
.list {
  overflow: auto;
  overflow-x: hidden;
  height: 100%;
  width: 100%;
}

.list-item {
  list-style: none;
  width: 100%;
}
</style>