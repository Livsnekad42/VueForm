<template>
  <div id="app">
    <VueForm />
  </div>
</template>

<script>
import VueForm from '@/components/VueForm';

export default {
  name: 'App',
  components: {
    VueForm
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
