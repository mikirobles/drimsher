<template>
  <div>
    <nuxt/>
  </div>
</template>

<style>
@font-face {
  font-family: "Avenir";
  src: url("../static/fonts/AvenirNextLTPro-Regular.woff2") format("woff2"),
    url("../static/fonts/AvenirNextLTPro-Regular.woff") format("woff");
  font-weight: normal;
  font-style: normal;
}

html {
  font-family: "Avenir", sans-serif, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 18px;
  line-height: 1.5;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  transition: 0.2s ease all;
  background-image: linear-gradient(-180deg, #E9EAFF 0%, #FFFFFF 77%);
}

*, *:before, *:after {
  box-sizing: border-box;
  margin: 0;
  font-size: 18px;
}
</style>
