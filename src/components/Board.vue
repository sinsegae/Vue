<template>
  <div>
    <Header/>
    <Body :dataOfChild="dataOfParants" @changeToActive="changeToActive"/>
    <Footer :dataOfChild="dataOfParants" @revertToActive="revertToActive" :activeItem="activeItem" />
  </div>
</template>

<script>
import Header from './Header.vue'
import Body from './Body.vue'
import Footer from './Footer.vue'
import read_data from '../data/read_data.js'

  export default {
    components: {
      Header,
      Body,
      Footer
    },
    data() {
      return {
        dataOfParants: read_data,
        activeItem : null
      }
    },
    methods : {
      changeToActive(index){
        this.activeItem = index
      },
      revertToActive() {
        this.activeItem = null 
      }
    }
  }
</script>
