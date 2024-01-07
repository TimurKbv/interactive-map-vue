<script setup>
import Members from './buildingInfo/Members.vue'
import { store } from '../../store/Store';
import IBuilding from '../../models/IBuilding'

const props = defineProps({
    id: String,
    Name: String,
    Coordinates: Object,
    size: Object,
    image: String,
    occupied: Number,
    empty: Number,
    address: String
});


function buildingDetailsHandler(e) {
    console.log(props);

    if (props.id === store.buildingDetails?.id) {
        store.buildingDetails = null;
        store.buildingDetailsStatus = false
    } else {
        store.buildingDetails = props;
        store.buildingDetailsStatus = true
        store.buildingArt =  IBuilding.building
    }
}
</script>

<template>

    <button 
    @click="buildingDetailsHandler"
    class=" bg-zinc-600 absolute border-8 border-green-400 text-center text-white text flex  flex-wrap items-center justify-center hover:scale-95 hover:bg-sky-500 transition-all duration-300 cursor-pointer" 
    v-bind:class="{'border-red-400': occupied !== empty }"
    v-bind:style="{
        width: Coordinates.Width + 'px' ,
        height: Coordinates.Length + 'px',
        top: Coordinates.Y + 'px',
        left: Coordinates.X + 'px',
    }">
        <span class="px-10"> {{ Name }} </span>

        <Members :members="occupied" />

    </button>

</template>



<style>

</style>