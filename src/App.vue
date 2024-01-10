<script>
import AppLoader from './components/AppLoader.vue';
import AppHeader from './components/AppHeader.vue';
import AppCards from './components/AppCards.vue';
import { store } from './store';
import axios from 'axios';
export default {
  components:{
    AppHeader,
    AppLoader,
    AppCards
  },
  data() {
    return {
      store
    }
  },
  methods: {
    getCards(){
      axios.get(store.endpoint).then( response =>{
        store.cardsList = response.data.data
        store.loaded = true;
      })
    }
  },
  created() {
    this.getCards();
  }
}
</script>
<template lang="">
  <AppHeader/>
  <main v-if="store.loaded">
    <div class="container" >
      <div class="row gy-4 my-2">
        <AppCards/>
      </div>
    </div>
  </main>
  <AppLoader v-else />
</template>
<style lang="scss">
@use './styles/generals.scss';
  
</style>