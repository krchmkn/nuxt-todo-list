<template>
  <div class="wrapper">
    <div class="top"></div>

    <div class="card">
      <div class="card__header">
        <h1 class="card__title">Todo list</h1>
        <AppButton @click="add(Date.now())">Add</AppButton>
      </div>

      <div class="card__content">
        <AppList :list="list" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const list = ref<Array<ListItem>>([])

let audio: HTMLAudioElement
onBeforeMount(() => {
  audio = new Audio('/add.mp3')
  audio.volume = .2;
})

function add(id: number) {
  const text = `Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do`

  list.value.push({
    id,
    title: text,
    ...(id % 2 === 0 ? { subtitle: text } : {})
  })

  if (audio) {
    audio.play()
  }
}

for (let i = 1; i <= 10; ++i) add(i);
</script>

<style lang="scss" scoped>
.wrapper {
  position: relative;
  min-width: 330px
}
.top {
  display: block;
  width: 330px;
  height: 110px;
  position: absolute;
  left: 0;
  top: -41px;
  background: top left / contain no-repeat url(@/assets/img/card-top.svg);
}

.card {
  position: relative;
  z-index: 1;
  display: grid;
  grid-template-rows: auto 1fr;
  gap: 30px;
  height: 540px;
  background: $gray;
  padding: 30px 15px;
  box-shadow: 0px 14px 34px rgba(0, 0, 0, 0.25);
  border-radius: 20px 0px 40px;
  overflow: hidden;

  &__header {
    display: grid;
    grid-template-columns: 1fr auto;
    padding: 0 15px;
  }

  &__title {
    font-style: normal;
    font-weight: 700;
    font-size: 28px;
    line-height: 34px;
  }

  &__content {
    overflow: hidden;

    &:after {
      content: "";
      position: absolute;
      bottom: 0;
      left: 20px;
      right: 20px;
      background: linear-gradient(180deg, rgba(37, 46, 66, 0) 0%, $gray 67.19%);
      height: 75px;
    }
  }
}

@media (min-width: 430px) {
  .wrapper {
    width: 420px;
    margin: 0 auto;
  }

  .top {
    width: 400px;
  }
}
</style>
