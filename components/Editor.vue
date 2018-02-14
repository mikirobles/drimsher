<template>
    <div>
        <textarea v-model="editorText" type="text" placeholder="Escribe aquí tu sueño." />
        <p v-bind:class="exceededLimit ? 'exceeded' : ''">{{ charsLeft }}</p>
    </div>
</template>

<script>
const charsLimit = 450;
export default {
  data: () => ({
    editorText: ""
  }),
  computed: {
    charsLeft() {
      return `${this.editorText.length} / ${charsLimit}`;
    },
    exceededLimit() {
      return this.editorText.length > charsLimit;
    }
  }
};
</script>

<style scoped>
.exceeded {
  background-image: linear-gradient(-180deg, #ff0303 0%, #bd1313 100%);
}
</style>

