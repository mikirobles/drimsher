<template>
    <article>
        <textarea v-model="editorText" type="text" placeholder="Escribe aquí tu sueño." />
        <div class="info">
          <span v-bind:class="exceededLimit ? 'exceeded' : ''">{{ charsLeft }}</span>
          <button v-bind:disabled="!sendAvailable" v-on:click="publish"><img v-bind:class="!sendAvailable ? 'disabled' : ''" src="../static/icons/send.svg" alt=""></button>
        </div>
    </article>
</template>

<script>
import fetch from 'isomorphic-fetch';
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
    },
    sendAvailable() {
      return (
        this.editorText.length <= charsLimit && this.editorText.length > 20
      );
    }
  },
  methods: {
    publish() {
      fetch('https://drimsher-backend-myvzbjpxev.now.sh/api/v1/post', {
        method: "POST",
        headers: {
			    "Content-Type": "application/json"
        },
        body: JSON.stringify({
          content: this.editorText
        })
      }).then(res => res.json()).then(console.log)
    }
  }
};
</script>

<style lang="scss" scoped>
textarea {
  width: 100%;
  height: 45vh;
  max-height: 300px;
  padding: 0.5em;
  border: 0;
  resize: none;
  color: #550b39;
  &:focus {
    outline: none;
  }
}

.exceeded {
  background-image: linear-gradient(-180deg, #ff0303 0%, #bd1313 100%);
}

.info {
  margin-top: 0.5em;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
}

.disabled {
  opacity: 0.2;
}
</style>

