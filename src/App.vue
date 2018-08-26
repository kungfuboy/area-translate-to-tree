<template>
  <div id="app">
    <HelloWorld :imgList="list" :showTime="7000"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  data() {
    return {
      list: [
        'https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=353311204,1638298436&fm=26&gp=0.jpg',
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1535031059913&di=6da68ae26c59cef9101a85a34668c2a3&imgtype=0&src=http%3A%2F%2Fimg5q.duitang.com%2Fuploads%2Fitem%2F201506%2F17%2F20150617132948_Usw3c.thumb.700_0.jpeg',
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1535031059913&di=60db598131e99611034d94c505e77783&imgtype=0&src=http%3A%2F%2Fscdn.file1.gk99.com%2Fphoto%2F2012-05%2F2012-05-22133765044676162.jpg',
        'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1535031059913&di=3b1a67c52a902f2c22c59d6ceb4b0645&imgtype=0&src=http%3A%2F%2Fd.paper.i4.cn%2Fmax%2F2017%2F04%2F01%2F10%2F1491013430122_759262.jpg'
      ]
    }
  },
  components: {
    HelloWorld
  }
}
</script>

<style>
body {
  margin: 0;padding: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
