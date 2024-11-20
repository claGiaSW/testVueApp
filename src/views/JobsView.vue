<script setup>
import JobListings from '@/components/JobListings.vue';
</script>

<template>
    <JobListings :limit="3" :showButton="true" />
</template>