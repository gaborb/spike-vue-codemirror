<template>
  <div id="app">
    <codemirror ref="myCm"
                :value="code" 
                :options="cmOptions"
                @ready="onCmReady"
                @focus="onCmFocus"
                @input="onCmCodeChange">
    </codemirror>
  </div>
</template>

<script>
// language js
import 'codemirror/mode/javascript/javascript.js'
// theme css
// import 'codemirror/theme/base16-dark.css'
// more codemirror resources
import 'codemirror/addon/lint/lint.js'
import 'codemirror/addon/lint/lint.css'
// import 'jshint'
// import 'codemirror/addon/lint/javascript-lint.js'
import jsonlint from 'jsonlint/lib/jsonlint.js'
window['jsonlint'] = jsonlint
import 'codemirror/addon/lint/json-lint.js'

export default {
  name: 'app',
  data () {
    return {
      code: JSON.stringify(JSON.parse('{"total":25,"limit":10,"skip":0,"data":[{"_id":"5968fcad629fa84ab65a5247","first_name":"Sabrina","last_name":"Mayert","address":"69756 Wendy Junction","phone":"1-406-866-3476 x478","email":"donny54@yahoo.com","updatedAt":"2017-07-14T17:17:33.010Z","createdAt":"2017-07-14T17:17:33.010Z","__v":0},{"_id":"5968fcad629fa84ab65a5246","first_name":"Taryn","last_name":"Dietrich","address":"42080 Federico Greens","phone":"(197) 679-7020 x98462","email":"betty_schaefer1@gmail.com","updatedAt":"2017-07-14T17:17:33.006Z","createdAt":"2017-07-14T17:17:33.006Z","__v":0}]}'), null, "  "),
      cmOptions: {
        // codemirror options
        tabSize: 4,
        mode: 'application/json',
        // theme: 'base16-dark',
        lineNumbers: true,
        line: true,
        // more codemirror options, 更多 codemirror 的高级配置...
        gutters: ['CodeMirror-lint-markers'],
        lint: true
      }
    }
  },
  methods: {
    onCmReady(cm) {
      console.log('the editor is readied!', cm)
    },
    onCmFocus(cm) {
      console.log('the editor is focus!', cm)
    },
    onCmCodeChange(newCode) {
      console.log('this is new code', newCode)
      this.code = newCode
    }
  },
  computed: {
    codemirror() {
      return this.$refs.myCm.codemirror
    }
  },
  mounted() {
    console.log('this is current codemirror object', this.codemirror)
    // you can use this.codemirror to do something...
  }  
}
</script>

<style>
</style>
