<template>
    <div class="flex flex-col overflow-hidden rounded-xl shadow-xl ">
        <div>
            <img :src="character.image" alt="">
        </div>
        <div class="p-3">
            <h3 class="text-2x1 text-center">{{ character.name }}</h3>
        </div>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';

    const props = defineProps({

    character: {
        required:true,
        type: Object
        }

    })

</script>