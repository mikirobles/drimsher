<template>
  <section class="container">
    <header>
      <img src="icons/refresh.svg" alt="">
      <h1 class="logo">
        drimsher
      </h1>
      <img v-on:click="isEditor = !isEditor" src="icons/write.svg" alt="">
    </header>
    <transition name="fade" mode="out-in">
      <article key="dreamview" v-if="!isEditor">
          <p>{{dream}}</p>
      </article>
      <article key="editor" v-else>
        <textarea v-model="editorText" type="text" placeholder="Escribe aquí tu sueño." />
      </article>
    </transition>
  </section>
</template>

<script>
export default {
  head: {
    title: "drimsher"
  },
  data: () => ({
    dream: "Lorem ipsum dolor sit amet, at alienum fastidii vel, eu ius elit congue. Ad nam reque adolescens honestatis, per ex nostrud euripidis. Vim vidit disputando ei. Ad his ipsum reprimique, ex quis posidonium nam. \n Quando utinam delicatissimi nam cu, clita indoctum mei in. Harum urbanitas his eu, sit legere quaestio adipiscing ea. Quando utinam delicatissimi nam cu, clita indoctum mei in. Harum urbanitas his eu, sit legere quaestio adipiscing ea.",
    isEditor: false,
    editorText: ""
  })
}
</script>

<style lang="scss">
@font-face {
    font-family: 'Avenir';
    src: url('../static/fonts/AvenirNextLTPro-Regular.woff2') format('woff2'),
        url('../static/fonts/AvenirNextLTPro-Regular.woff') format('woff');
    font-weight: normal;
    font-style: normal;
}

* {
  font-family: 'Avenir', sans-serif;
  line-height: 1.5;
  font-size: 18px;
}

header {
  display: flex;
  padding: 1em 0;
  width: 100%;
  justify-content: space-between;
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
  background-image: linear-gradient(-180deg, #4BC3FD 0%, #B224FA 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}
article {
  font-weight: bold;
  width: 100%;
  min-height: calc( 100vh - 90px );
  padding-top: 5vh;
  p {
    white-space: pre-line;
    background-image: linear-gradient(-180deg, #550B39 0%, #640993 100%);
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
  color: #550B39;
  &:focus {
    outline: none;
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

</style>
