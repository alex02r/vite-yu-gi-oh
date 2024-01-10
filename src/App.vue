<script>
import AppHeader from './components/AppHeader.vue';
import AppCards from './components/AppCards.vue';
import { store } from './store';
import axios from 'axios';
export default {
  components:{
    AppHeader,
    AppCards
  },
  data() {
    return {

    }
  },
  mounted() {
    this.getCard()
  },
  methods: {
    getCard(){
      axios.get(store.endpoint).then( response =>(
        store.cardsList = response.data.data 
      ))
    }
  },
}
</script>
<template lang="">
  <AppHeader/>
  <main>
    <div class="container">
      <div class="row">
        <AppCards/>
      </div>
    </div>
  </main>
</template>
<style lang="scss" scoped>
@use './styles/generals.scss';
  
</style>