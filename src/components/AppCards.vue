<script>
import { store } from "../store";
export default {
    data() {
        return {
            store
        }
    }
}
</script>
<template lang="">
    <div class="col-6 col-md-4 col-lg-3"  v-for="(card, index) in store.cardsList" :key="index">
        <div class="card">
            <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
            <div class="card-body">
              <h5 class="card-title">{{ card.name }}</h5>
              <p class="card-text"> {{ card.archetype }}</p>
            </div>
          </div>
    </div>
</template>
<style lang="scss" scoped>
@use '../styles/generals.scss';
    
</style>