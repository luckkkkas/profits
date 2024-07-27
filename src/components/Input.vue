<template>
  <input type="text" v-model="props.label">
</template>

<script>
import { defineProps } from 'vue';

const props= defineProps({
    label: {
        required: true,
        type: 'string',
    }
});
</script>

<style>

</style>