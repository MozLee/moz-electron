<template>
  <div id="basic-audio">
    <Player v-for="(item,index) in audioList" :key="index" :name="item.name" :url="item.url" :keyCode="item.quickKey"></Player>
  </div>
</template>
<script>
import Player from '../components/Player'
import {
  data
} from '../audiolist/list.json'
export default {
  components: {
    Player
  },
  data () {
    return {
      audioList: data
    }
  }
}
</script>
<style lang="scss">
#basic-audio{
  display: flex;
  justify-items: center;
  justify-content: space-around;

  flex-wrap:wrap
}
</style>
