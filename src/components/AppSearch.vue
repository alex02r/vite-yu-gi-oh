<script>
import AppNumberResult from "./AppNumberResult.vue";
import { store } from "../store";
import axios from "axios";
export default {
    components:{
        AppNumberResult
    },
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
            let types = [];

            axios.get(store.endpointType).then(response =>{
                types = response.data;
                for (let i = 1; i <= 6; i++) {
                    let num = Math.floor(Math.random()* 526);
                    console.log(this.typeArray.includes(types[num].archetype_name));
                    if (!this.typeArray.includes(types[num].archetype_name)) {
                        this.typeArray.push(types[num].archetype_name)
                    }
                }
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
                    <option selected value="">Select archetype</option>
                    <option v-for="(type, index) in typeArray" :key="index" :value="type">{{ type }}</option>
                </select>
                <div class="btn btn-sm btn-dark" @click="$emit('filter')">Cerca</div>
                <div class="btn btn-sm btn-warning" @click="$emit('reset_select')">reset</div>
            </div>
        </div>
        <AppNumberResult/>
    </div>
</template>
<style lang="scss" scoped>
    @use '../styles/generals.scss';
</style>