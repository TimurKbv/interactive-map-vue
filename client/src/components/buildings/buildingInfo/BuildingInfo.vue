<script setup>

const props = defineProps({
    image: String,
    address: String,
    Name: String,
    occupied: Number,
    empty: Number
})

</script>

<template>
    <div class=" my-16 flex flex-col gap-3">
        <!-- Building image  -->
        <div class="w-full h-32 md:h-40 lg:h-54 xl:h-64 2xl:h-80 ">
            <img :src="image" alt="Building picture" class=" w-full h-full object-contain " />
        </div>
        <!-- Building details  -->
        <div class=' mx-5  '>
            <h2 class=" text-3xl mt-10 mb-5"> {{ Name }} </h2>
            <h3 class="text-xl font-bold"> Occupied:
                <span class="text-green-700" v-bind:class="{ 'text-red-800': occupied !== empty }"> {{ occupied }} </span>
            </h3>
            <h3 class="text-xl font-bold"> Empty: <span class="text-green-700"> {{ empty }} </span> </h3>
            <div class=' mt-10'>
                <h4 class='font-bold text-lg'>Address:</h4>
                <p> {{ address }} </p>
            </div>
        </div>
    </div>
</template>