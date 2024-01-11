<script>
import AppLoader from './components/AppLoader.vue';
import AppHeader from './components/AppHeader.vue';
import AppSearch from './components/AppSearch.vue';
import AppCards from './components/AppCards.vue';
import { store } from './store';
import axios from 'axios';
export default {
  components:{
    AppHeader,
    AppLoader,
    AppSearch,
    AppCards
  },
  data() {
    return {
      store
    }
  },
  methods: {
    getCards(){
      let url = store.endpoint;
        if (store.select != '') {
          url += `&archetype=${store.select}`
        }
      axios.get(url).then( response =>{
        store.luader = false;
        store.cardsList = response.data.data
        store.loaded = true;
      })
    },
    resetSelect(){
      store.select= '';
      axios.get(store.endpoint).then( response =>{
        store.luader = false;
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
      <AppSearch @filter="getCards" @reset_select="resetSelect"/>
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