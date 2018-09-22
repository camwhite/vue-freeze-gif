<template>
  <div id="app">
    <freeze source="https://emojis.slackmojis.com/emojis/images/1498862355/2559/cattyping.gif" />
  </div>
</template>

<script>
import Freeze from './components/Freeze'

export default {
  name: 'app',
  components: {
    Freeze
  }
}
</script>
<style lang="stylus">
#app
  width 256px
  height 256px
  margin auto
</style>
