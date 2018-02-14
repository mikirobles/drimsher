<template>
  <section class="container">
    <app-header :isEditor="isEditor" :switchMode="switchMode"/>
    <transition name="fade" mode="out-in">
      <article key="dreamview" v-if="!isEditor">
          <p>{{dream}}</p>
      </article>
      <editor v-else />
    </transition>
  </section>
</template>

<script>
import Editor from "../components/Editor";
import AppHeader from "../components/AppHeader";

export default {
  head: {
    title: "drimsher"
  },
  components: {
    Editor,
    AppHeader
  },
  data: () => ({
    dream:
      "Lorem ipsum dolor sit amet, at alienum fastidii vel, eu ius elit congue. Ad nam reque adolescens honestatis, per ex nostrud euripidis. Vim vidit disputando ei. Ad his ipsum reprimique, ex quis posidonium nam. \n Quando utinam delicatissimi nam cu, clita indoctum mei in. Harum urbanitas his eu, sit legere quaestio adipiscing ea. Quando utinam delicatissimi nam cu, clita indoctum mei in. Harum urbanitas his eu, sit legere quaestio adipiscing ea.",
    isEditor: false
  }),
  methods: {
    switchMode() {
      this.isEditor = !this.isEditor;
    }
  }
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
  transition: 0.2s ease all;
}

.container {
  padding: 0 25px;
  width: 100%;
  max-width: 870px;
  margin: auto;
  display: flex;
  flex-direction: column;
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
  p,
  span {
    white-space: pre-line;
    background-image: linear-gradient(-180deg, #550b39 0%, #640993 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    &::selection {
      background: rgba(61, 219, 95, 0.637);
    }
  }
}

button {
  border: none;
  background: none;
  display: flex;
  justify-content: center;
  align-items: center;
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
