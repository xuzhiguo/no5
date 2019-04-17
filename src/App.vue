<template>
  <div id="app">
    <MyHeader></MyHeader>
    <router-view/>
  </div>
</template>

<script>
import MyHeader from '#/MyHeader'
export default {
  name: 'App',
  components: {MyHeader}
}
</script>

<style lang="scss">
  @import '~/index';
</style>
