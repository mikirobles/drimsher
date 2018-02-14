<template>
    <header>
      <div class="buttons">
        <button v-if="!isEditor"><img key="refresh" src="icons/refresh.svg" alt="refresh"></button>
        <button v-else  v-on:click="switchMode"><img key="back" src="icons/back.svg" alt="go back"></button>
        <button v-on:click="switchMode"><img v-bind:class="isEditor ? 'hidden' : ''" src="icons/write.svg" alt=""></button>
      </div>
      <h1 class="logo">
        drimsher
      </h1>
    </header>
</template>

<script>
export default {
  props: {
    isEditor: Boolean,
    switchMode: Function
  }
};
</script>

<style lang="scss" scoped>
header {
  position: relative;
  margin: 1em 0;
  width: 100%;
  .logo {
    text-align: center;
  }
  .buttons {
    position: absolute;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
</style>


