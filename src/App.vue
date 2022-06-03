<template>
  <div id="app">
    <MyHead />
    <MyTodos />
  </div>
</template>

<script>
import MyHead from './components/MyHead.vue'
import MyTodos from './components/MyTodos.vue'
export default {
  name: 'App',
  components: { 
    MyHead, MyTodos
  }
}
</script>

<style>

</style>
