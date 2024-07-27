<template>
    <input type="text" v-model="topic">
    <button @click="addTopic">+</button>
    {{ lista }}
</template>

<script setup lang="ts">
import type { TopicItem } from '@/types/topics';
import { ref } from 'vue';

    const topic = ref<string>();
    const lista = ref<TopicItem>([]);
    let id = 0;
    function addTopic(){
        lista.value.push({
            nome: topic.value,
            id: id++
        });

        topic.value = '';
    }
</script>

<style>

</style>