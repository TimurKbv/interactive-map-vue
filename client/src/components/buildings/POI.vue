<script setup>
import { store } from '../../store/Store';
import IBuilding from '../../models/IBuilding'

const props = defineProps({
    id: String,
    name: String,
    Coordinates: Object,
    size: Object,
    image: String,
    description: String
})

function poiDetailsHandler(e) {

    if (props.id === store.poiDetails?.id) {
        store.poiDetails = null;
        store.buildingDetailsStatus = false
    } else {
        store.buildingArt =  IBuilding.poi
        store.poiDetails = props;
        store.buildingDetailsStatus = true
    }
}

</script>

<template>
    <button 
    @click="poiDetailsHandler"
        class="bg-zinc-600 absolute border  text-center text-white text flex items-center justify-center hover:scale-95 hover:bg-sky-500 transition-all duration-300 cursor-pointer"
        v-bind:style="{
            width: size.width + 'px' ,
            height: size.height + 'px',
            top: Coordinates.Y + 'px',
            left: Coordinates.X + 'px',
        }"
    >
        <span>{{ name }}</span>
    </button>
</template>