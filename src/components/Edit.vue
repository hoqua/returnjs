<template>
    <div>
        <div id="javascript-editor"></div>
    </div>
</template>

<script>
import * as ace from 'brace'
import 'brace/mode/javascript'
import 'brace/theme/dracula'
import 'brace/keybinding/emacs'
import 'brace/ext/language_tools'
import 'brace/snippets/javascript'

export default {
  name: 'Edit',
  mounted () {
    ace.acequire('ace/ext/language_tools')

    const editor = ace.edit('javascript-editor')
    editor.getSession().setMode('ace/mode/javascript')
    editor.setTheme('ace/theme/dracula')
    editor.setKeyboardHandler('ace/keyboard/emacs')
    editor.setShowPrintMargin(false)

    editor.setOptions({
      autoScrollEditorIntoView: true,
      enableBasicAutocompletion: false,
      enableSnippets: true,
      enableLiveAutocompletion: true,
      fontFamily: 'monospace',
      fontSize: '13px'
    })

    editor.getSession().on('change', () => {
      this.$emit('onChange', editor.getValue())
    })
  }
}
</script>

<style scoped>
    #javascript-editor {
        margin: 0;
        position: absolute;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        width: 50%;
        height: 100vh;
    }
</style>
