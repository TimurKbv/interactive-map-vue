<script setup>
import BuildingsInfo from './buildingInfo/BuildingInfo.vue'
import PInfo from './buildingInfo/PInfo.vue'
import { store } from '../../store/Store';
import IBuilding from '../../models/IBuilding';

function closeDetails() {
  store.buildingDetailsStatus = false;
}

</script>

<template>
  <section class="fixed top-[16.6vh] bottom-[8.3vh] right-0 bg-slate-400 w-3/12 overflow-auto border-l-2 border-white"
    v-bind:class="{ 'hidden': store.buildingDetailsStatus === false }">
    <BuildingsInfo v-if="store.buildingArt === IBuilding.building && store.buildingDetails"
      :image="store.buildingDetails.image" :occupied="store.buildingDetails.occupied"
      :address="store.buildingDetails.address" :Name="store.buildingDetails.Name" :empty="store.buildingDetails.empty" />

    <PInfo v-if="store.buildingArt === IBuilding.poi && store.poiDetails" :image="store.poiDetails.image"
      :name="store.poiDetails.name" :description="store.poiDetails.description" />

    <!-- CLOSE BUTTON -->
    <div @click="closeDetails"
      className="absolute right-0 top-0 text-2xl px-4 py-2 flex  hover:text-red-500 transition-all text-black cursor-pointer">
      <!-- Close Logo -->
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="w-6 h-6">
        <path fill-rule="evenodd"
          d="M5.47 5.47a.75.75 0 0 1 1.06 0L12 10.94l5.47-5.47a.75.75 0 1 1 1.06 1.06L13.06 12l5.47 5.47a.75.75 0 1 1-1.06 1.06L12 13.06l-5.47 5.47a.75.75 0 0 1-1.06-1.06L10.94 12 5.47 6.53a.75.75 0 0 1 0-1.06Z"
          clip-rule="evenodd" />
      </svg>

    </div>
  </section>
</template>