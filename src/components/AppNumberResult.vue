<script>
import { store } from "../store";
export default {
    data() {
        return {
            store
        }
    },
    computed:{

    }
    
}
</script>
<template lang="">
    <div calss="col-4" v-if="store.select">
        <span class="badge text-bg-secondary" v-if="store.cardsList.length > 0">{{ store.cardsList.length }} results</span>
        <span class="badge rounded-pill text-bg-secondary" v-else>No results</span>
    </div>
</template>
<style lang="">
    
</style>