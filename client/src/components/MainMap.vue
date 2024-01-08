<script setup>
import { onMounted, ref } from 'vue';
import Building from './buildings/building.vue'
import POI from './buildings/POI.vue'
import Details from './buildings/Details.vue'


const buildings = ref([])
const pois = ref([])

onMounted(async () => {

    setTimeout(async () => {
        const res = await fetch("http://localhost:8080/")
        const json = await res.json()

        buildings.value = json[0].Buildings
        pois.value = json[0].POIs
    }, 2000);

})
</script>

<template>

    <div  v-if="buildings.length > 1"
        class="w-full relative bg-gray-200 col-start-2 col-span-7 row-start-3 row-span-9 overflow-scroll">

        <!-- Buildings -->
        <Building v-for="b in buildings" :-coordinates="b.Coordinates" :id="b.id" :-name="b.Name" :empty="b.empty"
            :image="b.image" :address="b.address" :occupied="b.occupied" />

        <!-- Streets -->
        <div className="absolute top-56 bg-gray-400 w-[3100px] h-40"></div>
        <div className="relative top-56 left-[1100px]  bg-gray-400 w-40 h-screen"></div>
        <div className="absolute top-[1000px] bg-gray-400 w-[3100px] h-40"></div>
        <!-- POIs -->
        <POI v-for="b in pois" :id="b.id" :name="b.Name" :Coordinates="b.Coordinates" :size="b.size" :image="b.image"
            :description="b.description" />
        <!-- Details -->
        <Details />

    </div>
    

    <!-- Loading  -->
    <h1 v-else className="text-center mt-28 text-9xl col-start-2 col-span-7 row-start-3 row-span-9 ">
        Loading...
    </h1>

</template>

