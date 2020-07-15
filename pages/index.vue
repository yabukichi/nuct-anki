<template>
  <div class="container">
    <div class="grid grid-cols-3 gap-2">
      <li v-for="n of 8">
        <div class="max-w-sm rounded overflow-hidden shadow-lg">
          <router-link to="/subject/cats">
            <div class="px-3 py-2">
              <div class="font-bold text-xl mb-2">カテゴリー名</div>
            </div>
          </router-link>
        </div>
      </li>
    </div>

    <div class="flex pt-10">
      <button class="ml-5 bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
        CSV
      </button>
      <router-link to="/create">
        <button class="ml-5 bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 hover:border-blue-500 rounded">
          add
        </button>
      </router-link>
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
}

.all-category{
  grid-template: 
  repeat(2, 200px) / 
  repeat(4, 1fr);
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
