<template>
  <div class="audio-player">
    <el-button type="primary" plain @click="play">{{name}}</el-button>
    <br>
    <el-tag type="info">快捷键{{keyCode}}</el-tag>
    <!-- <el-select v-model="keyValue" placeholder="选择快捷键" @change="changeQuick">
      <el-option v-for="item in quickKey" :key="item.value" :label="item.label" :value="item.value" >
      </el-option>
    </el-select> -->
  </div>
</template>
<script>
export default {
  name: 'Player',
  props: {
    name: {
      type: String,
      required: true
    },
    url: {
      type: String,
      required: true
    },
    keyCode: {
      type: Number,
      required: true
    }
  },
  data () {
    return {
      keyValue: '',
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
  methods: {
    play () {
      console.log('播放')
      let audio = document.createElement('audio')
      audio.src = this.url
      audio.play()
      audio = null
    },
    changeQuick () {
      // console.log(this.$store.commit('setRegisterKey', this.keyValue))
      // if (this.$store.commit('setRegisterKey', this.keyValue)) {
      //   alert('快捷键绑定成功')
      // } else {
      //   alert('快捷键已被绑定')
      // }
    }
  },
  created () {
    window.addEventListener('keydown', (e) => {
      console.log(e.keyCode, this.keyCode)
      if (e.keyCode - 48 === this.keyCode) {
        this.play()
      }
    })
  }
}
</script>
<style lang="scss">
.audio-player{
  margin:10px;
  text-align: center;
}
</style>
