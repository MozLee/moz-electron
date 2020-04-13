<template>
  <div id="app">
    <Nav></Nav>
    <router-view></router-view>
  </div>
</template>

<script>
import Nav from './views/Nav'
const { join } = require('path')
const fs = require('fs')
export default {
  name: 'app',
  components: {
    Nav
  },
  created () {
    function findSync (startPath) {
      const result = []

      function finder (path) {
        const files = fs.readdirSync(path)

        files.forEach((val, index) => {
          const fPath = join(path, val)

          const stats = fs.statSync(fPath)

          if (stats.isDirectory()) finder(fPath)
          // const re = /publick/
          if (stats.isFile()) {
            if (!fPath.includes('.DS_Store')) { result.push(fPath) }
          }
        })
      }

      finder(startPath)
      return result
    }

    const fileNames = findSync('./public/audio')
    console.log(fileNames)
    const data = fileNames.map((v, index) => {
      return {
        name: v.match(/^\/(\w+)|([\u4e00-\u9fa5]+)|([0-9]+)\./i)[0],
        url: v.replace(/public/, ''),
        quickKey: index <= 8 ? index + 1 : undefined
      }
    })
    console.log(data)
    const audiolist = {
      title: '音效列表',
      data
    }
    fs.writeFileSync(join('./src/audiolist/list.json'), JSON.stringify(audiolist))
    // fileNames.forEach((v) => {
    //   console.log(v)
    //   console.log(v.match(/^\/(\w+)|([\u4e00-\u9fa5]+)|([0-9]+)\./i))
    // })
    // console.log(fs)
    // console.log(fileNames)
    // fs.writeFileSync(join('./src/audiolist/list.json'), {})
  }
}
</script>
<style lang="scss">
@import "@/assets/css/reset.scss";
</style>
