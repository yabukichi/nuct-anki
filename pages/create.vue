<template>
  <div class="container">
    <div class="p-5">
      <li v-for="n of 8" class="m-auto my-5 p-5 rounded shadow-lg">
        <div class="overflow-hidden">
          <div class="px-3 py-3 my-5 m-auto rounded shadow-lg">
            <div class="font-bold text-xl mb-2">Q.{{ n }}</div>
          </div>
          <div class="px-3 py-3 my-5 m-auto rounded shadow-lg">
            <div class="font-bold text-xl mb-2">A.{{ n }}</div>
          </div>
        </div>
      </li>
    </div>
    <router-link to="/">
      <button class="ml-5 bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        TOP
      </button>
    </router-link>
    <router-link to="/">
      <button class="ml-5 bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        ALL SUBJECT!
      </button>
    </router-link>
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
.container {
  margin: 0 auto;
  width: 1024px; 
  text-align: left;
}
li{
  list-style: none;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
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
