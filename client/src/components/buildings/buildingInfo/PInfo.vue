<script setup>

  const props = defineProps({
    name: String,
    image: String,
    description: String
  })

</script>

<template>

<div class=" my-16 flex flex-col gap-3">
      <!--  POI image  -->
        <div class="w-full h-32 md:h-40 lg:h-54 xl:h-64 2xl:h-80 ">
            <img :src="image" alt="POI picture" class=" w-full h-full object-contain " />
        </div>
        <!-- POI description -->
        <div class="mx-5">
            <h2 class=" text-xl xl:text-3xl mt-10"> {{ name }} </h2>
            <p class="text-xs md:text-md xl:text-lg"> {{ description }} </p>
        </div>
  </div>

</template>