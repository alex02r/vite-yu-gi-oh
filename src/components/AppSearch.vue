<script>
import { store } from "../store";
import axios from "axios";
export default {
    data() {
        return {
            store,
            typeArray: []
        }
    },
    created() {
        this.getTypeArray()
    },
    methods: {
        getTypeArray(){
            //get all archetypes
            let types = [];
            axios.get(store.endpointType).then(response =>{
                types = response.data;
                types.forEach(element => {
                    for (let i = 0; i < store.cardsList.length; i++) {
                    if (element.archetype_name == store.cardsList[i].archetype) {
                        if (!this.typeArray.includes(store.cardsList[i].archetype)) {
                            this.typeArray.push(store.cardsList[i].archetype)
                            console.log(this.typeArray);
                        }
                    }
                }
                });
                
            })
            
            
        }
    },
}
</script>
<template lang="">
    <div class="row">
        <div class="col-4">
            <select class="form-select form-select-sm" aria-label="Small select example">
                <option selected>Select archetype</option>
                <option v-for="(type, index) in typeArray" :key="index" :value="type">{{ type }}</option>
            </select>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';
</style>