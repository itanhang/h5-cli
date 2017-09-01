<template>
  <div id="container">
    <img src="./assets/logo.png" class="logo">
    <page></page>
  </div>
</template>

<script>
import Page from './components/page'

export default {
  name: 'app',
  data () {
    return {
    }
  },
  components: {
    Page
  }
}
</script>

<style lang="less">
#container {
  position: fixed;
  width: 100%;
  height: 100%;
  background: url('./assets/bg.jpg') center no-repeat;
  background-size: cover;
}
.page-wraper, .page {
  width: 100%;
  height: 100%;
}
.page {    
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 50px;
  margin: auto;
  opacity: 0.5;
  width: 15%;
}
</style>
