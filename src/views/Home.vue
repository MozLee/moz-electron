<template>
<div class="home">
  <div class="audio-container" v-for="item in audioList" :key="item.name">
    <el-button type="primary" plain @click="play(item.url)">{{item.name}}</el-button>
    <el-select v-model="keyValue" placeholder="请选择">
      <el-option v-for="item in quickKey" :key="item.value" :label="item.label" :value="item.value" >
      </el-option>
    </el-select>
  </div>
</div>
</template>

<script>
// @ is an alias to /src
import {
  data
} from '../audiolist/list.json'
export default {
  name: 'Home',
  components: {},
  data () {
    return {
      audioList: data,
      keyValue: 0,
      quickKey: [
        {
          value: 48,
          label: '1'
        },
        {
          value: 49,
          label: '2'
        },
        {
          value: 50,
          label: '3'
        },
        {
          value: 51,
          label: '4'
        }, {
          value: 52,
          label: '5'
        }, {
          value: 53,
          label: '6'
        }, {
          value: 54,
          label: '7'
        },
        {
          value: 55,
          label: '8'
        }, {
          value: 56,
          label: '9'
        }
      ]
    }
  },
  computed: {

  },
  methods: {
    play (url) {
      console.log(url)
      // const audio = document.querySelector('#a-shua')
      // audio.play()
      let audio = document.createElement('audio')
      audio.src = url
      audio.play()
      audio = null
    }
  },
  created () {
    window.addEventListener('keydown', (e) => {
      if (e.keyCode >= 48 && e.keyCode <= 57) {
        const index = e.keyCode - 49
        console.log(index)
        this.play(this.audioList[index].url)
      }
    })
  }
}
</script>

<style lang="scss">
.home {
  display: flex;
}
</style>
