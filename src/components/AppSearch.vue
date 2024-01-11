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
                        }
                    }
                }
                });
                
            })
            
            
        },
    },
}
</script>
<template lang="">
    <div class="row mt-3">
        <div class="col-4">
            <div class="d-flex gap-3">
                <select class="form-select form-select-sm" v-model="store.select">
                    <option selected>Select archetype</option>
                    <option v-for="(type, index) in typeArray" :key="index" :value="type">{{ type }}</option>
                </select>
                <div class="btn btn-sm btn-dark" @click="$emit('filter')">Cerca</div>
                <div class="btn btn-sm btn-warning" @click="$emit('reset_select')">reset</div>
            </div>
        </div>
        <div class="col-4">
        </div>
    </div>
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';
</style>