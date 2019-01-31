<template>
 <div id="output" ref="output"></div>
</template>

<script>
import JSONFormatter from 'json-formatter-js'

export default {
  props: ['code'],
  name: 'Output',
  data () {
    return {
      html: null
    }
  },
  methods: {
    getCode (code) {
      let codeResult
      try {
        // eslint-disable-next-line
        codeResult = eval(code)
      } catch (e) {
        codeResult = e.message
      }
      console.log(codeResult)
      const output = this.$refs.output
      const formatter = new JSONFormatter(codeResult, 1, { theme: 'dark' })
      // eslint-disable-next-line
      output.childElementCount > 0 ? output.children[0].remove() : null
      output.appendChild(formatter.render())
    }
  },
  watch: {
    code: {
      handler: 'getCode'
    }
  }
}
</script>

<style>
    #output{
        position: absolute;
        left: 50%;
        top: 0;
        width: 50%;
        height: 100vh;
        background-color: #282a36;
        padding-left: 10px;
    }
</style>
