<script setup>
    import { defineProps } from 'vue';

    defineProps({
       background: {
        type: String,
        default: "bg-grey-100"
       } 
    })
</script>

<template>
    <div :class="`${background} p-6 rounded-lg shadow-md`">
        <slot></slot>
    </div>
</template>