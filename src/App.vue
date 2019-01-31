<template>
  <div id="app">
    <edit @onChange="val => code = val"></edit>
    <div  class="separator"/>
    <output-j-s :code="code"/>
  </div>
</template>

<script>
import Edit from './components/Edit'
import OutputJS from './components/OutputJS'
export default {
  name: 'app',
  components: { OutputJS, Edit },
  data () {
    return {
      code: ''
    }
  }
}
</script>

<style>
  body {
    margin: 0 !important;
  }
  .separator {
    z-index: 9999;
    height: 95vh;
    width: 1px;
    background: #31F031;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translateY(-50%);
  }
  #app{
    position: relative;
    height: 100vh;
    width: 100vw;
    overflow-x: hidden;
  }
</style>
