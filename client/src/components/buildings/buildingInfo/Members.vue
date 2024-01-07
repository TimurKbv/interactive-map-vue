<script setup>
    defineProps({
        members: Number
    })
</script>

<template>
        <div class="flex gap-3">
       <!-- people logo  -->
      <div class="text-2xl"> Logo </div>
      <span> {{ members }} </span>
    </div>
</template>