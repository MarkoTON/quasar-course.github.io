<template>
  <q-page padding>
    <input type="text" @keyup.esc="clearMessage" @keyup.enter="alertMessage" v-model="message" placeholder="There is no message now in it">
    <button @click="clearMessage">Clear input</button>
    <h5 class="border-gray" v-if="message.length">{{ message }}</h5>
    <!-- It's removing both -->
    <h5 class="border-gray" v-show="message.length">{{ message }}</h5>
    <p>Metallica</p>
    <p>Uppercase message from methods: {{ this.messageUpper() }}</p>
    <p>Uppercase message from computed: {{ messageToUpp }}</p>
    <p>Filter message: {{ message | capitalize }}</p>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  // name: 'PageIndex'
  data(){
    return {
      message: 'I love Vue.js'
    }
  },
  computed:{
    messageToUpp(){
      return this.message.toUpperCase()
    }
  },
  methods:{
    clearMessage(){
      this.message = ''
    },
    handleKeyUp(e){
      console.log(e.keyCode)
      if(e.keyCode === 27){
        console.log("Metallica")
        console.log("Metallica")
        this.clearMessage()
        console.log(this.message)
      } else if(e.keyCode == 13){
        alert(this.message)
      }
    },
    alertMessage(){
      alert(this.message)
    },
    messageUpper(){
      return this.message.toUpperCase()
    }
  },
  filters: {
    messageLowercase(value){
      console.log(value)
      console.log("Nirvana")
      return value.toLowerCase()
    },
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
})
</script>

<style>
.border-gray {
  border: 2px solid gray;
}
</style>
