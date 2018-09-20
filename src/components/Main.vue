<template>

  <div class="container">


    <Popup v-if="showPopup" :size="size" :text="text" @close="showPopup = false" />

    <div class="wrapper">
      <button  type="button" class="btn-preview" @click="showPopup = true">Preview </button>



      <select v-model="size" @change="calculateText">
        <option :value="13">13.3 inch</option>
        <option :value="17">17 inch</option>
        <option :value="40">40 inch</option>
      </select>

    <vue-editor v-model="text" rows="9"></vue-editor>
    <span>{{ counter }} / {{ max }}</span>

    <!-- <textarea ref="text" v-model="text" :maxlength="max" rows="9" /> -->

    </div>
  </div>
</template>

<script>
import Popup from './Popup'
import { VueEditor } from 'vue2-editor'

export default {
  name: 'Main',

  components: {
    Popup,
    VueEditor
  },

  data () {
    return {
      showPopup: false,
      text: '',
      size: 13,
      max: 500
    }
  },

  computed: {
    counter () {
      return this.strip(this.text).length
    }
  },

  watch: {
    text (value, old) {
      let txt = this.strip(value)
      if (this.max  < txt.length) {
        this.text = old
      }
    }
  },

  methods: {
    strip (html) {
       let tmp = document.createElement('div')
       tmp.innerHTML = html
       return tmp.textContent || tmp.innerText || ''
    },

    calculateText () {
      let maxLen = {
        13: 500,
        17: 900,
        40: 2400
      }
      this.max = maxLen[this.size]
      console.log(this.max);


    }

}

}

</script>

<style scoped>
  .container { width: 100%; height: 100%; }

  .wrapper { width: 100%; max-width: 700px; margin: 0 auto; margin-top: 100px;}

  select { width: 100%; height: 40px; }

  button { height: 40px; padding: 0 30px; float: right; margin-bottom: 20px; }

  vue-editor{ width: 100%; padding: 15px; box-sizing: border-box; margin-top: 20px; }
  .btn-preview{ background-color: #42b983; cursor: pointer; }

  span { display: block; text-align: right; }
</style>
