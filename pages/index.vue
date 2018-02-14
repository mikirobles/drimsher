<template>
  <section class="container">
    <header>
      <div class="buttons">
        <img key="refresh" v-if="!isEditor" src="icons/refresh.svg" alt="refresh">
        <img key="back" v-on:click="isEditor = !isEditor" v-else src="icons/back.svg" alt="go back">
        <img v-bind:class="isEditor ? 'hidden' : ''" v-on:click="isEditor = !isEditor" src="icons/write.svg" alt="">
      </div>
      <h1 class="logo">
        drimsher
      </h1>
    </header>
    <transition name="fade" mode="out-in">
      <article key="dreamview" v-if="!isEditor">
          <p>{{dream}}</p>
      </article>
      <article key="editor" v-else>
        <editor @update-editor-text="(text) => {editorText = text}" />
      </article>
    </transition>
  </section>
</template>

<script>
import Editor from "../components/Editor";
export default {
  head: {
    title: "drimsher"
  },
  components: {
    Editor
  },
  data: () => ({
    dream:
      "Lorem ipsum dolor sit amet, at alienum fastidii vel, eu ius elit congue. Ad nam reque adolescens honestatis, per ex nostrud euripidis. Vim vidit disputando ei. Ad his ipsum reprimique, ex quis posidonium nam. \n Quando utinam delicatissimi nam cu, clita indoctum mei in. Harum urbanitas his eu, sit legere quaestio adipiscing ea. Quando utinam delicatissimi nam cu, clita indoctum mei in. Harum urbanitas his eu, sit legere quaestio adipiscing ea.",
    isEditor: false
  })
};
</script>

<style lang="scss">
@font-face {
  font-family: "Avenir";
  src: url("../static/fonts/AvenirNextLTPro-Regular.woff2") format("woff2"),
    url("../static/fonts/AvenirNextLTPro-Regular.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

* {
  font-family: "Avenir", sans-serif;
  line-height: 1.5;
  font-size: 18px;
}

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
.container {
  min-height: 100vh;
  padding: 0 9vw;
  width: 100%;
  max-width: 870px;
  margin: auto;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.logo {
  font-size: 2em;
  letter-spacing: 0.17px;
  background-image: linear-gradient(-180deg, #4bc3fd 0%, #b224fa 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
article {
  font-weight: bold;
  width: 100%;
  min-height: calc(100vh - 90px);
  padding-top: 5vh;
  p {
    white-space: pre-line;
    background-image: linear-gradient(-180deg, #550b39 0%, #640993 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
}

textarea {
  width: 100%;
  height: 50vh;
  padding: 0.5em;
  border: 0;
  resize: none;
  color: #550b39;
  &:focus {
    outline: none;
  }
}

.hidden {
  opacity: 0;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
