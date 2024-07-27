<template>
    <input type="text" v-model="topic">
    <button @click="addTopic">+</button>

    <ul>
        <li class="list" v-for="topic in lista" :key="topic.id"> 
            <input v-model="checked" :class="[checked ? 'checked' : 'noChecked']" type="checkbox"> 
            {{ topic.name }}
        </li>
    </ul>
    {{ lista }}
</template>

<script setup lang="ts">
import type { TopicItem } from '../types/topics';
import { ref } from 'vue';

const checked = false;




    const topic = ref<string>();
    const lista = ref<TopicItem[]>([]);
    let id = 0;


    function addTopic(){
        if(typeof topic.value !== 'string' || topic.value == undefined){
            alert('inválido2')
            return null
        }
        lista.value.push({
            name: topic.value,
            id: id++,
        });

        topic.value = '';
    }


    
</script>

<style>

.list{
    list-style: none;
}

.checked{
    text-decoration: line-through;
}
.noChecked{
    text-decoration: none;
}
</style>