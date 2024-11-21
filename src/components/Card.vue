<script setup lang="ts">
import { defineProps } from 'vue';

interface Props {
    background: string;
}

const { background = "bg-grey-100" } = defineProps<Props>();

</script>

<template>
    <div :class="`${background} p-6 rounded-lg shadow-md`">
        <slot></slot>
    </div>
</template>