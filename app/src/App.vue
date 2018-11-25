<template>
  <div id="app">
      <main role="main" class="main">
          <app-form />
      </main>
  </div>
</template>

<script>
import AppForm from './components/AppForm.vue'

export default {
  name: 'app',
  components: {
    AppForm
  }
}
</script>
<style>
    .main {
        background: #fafafa;
        min-height: 100vh;
    }
</style>
