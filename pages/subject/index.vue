<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        edit
      </h1>
      <h2 class="subtitle">
        My solid Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  }
}
</script>

<style lang="scss" scope>
li{
  list-style: none;
}

.container {
  margin: 0 auto;
  width: 1024px;
  text-align: center;
  height: 100vh;
  display: flex;
  flex-flow: column;
}

.ankicard{
  border: solid 2px #dcdcdc;
  position: relative;
}

.number{
  position: absolute;
  top: 5px;
  left: 5px;
}

.anki-contents{
  width: 700px;
  height: auto;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 40px;
  color: #35495e;
  letter-spacing: 1px;
  .type{
    padding : 5px 10px;
    color: blue;
  }
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
