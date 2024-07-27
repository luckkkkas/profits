<template>
  <h1>listagem</h1>
  <input type="text" placeholder="Ingrediente" v-model="ingrediente"><br>
  <input type="number" placeholder="quantidade usado" v-model="quantidade"><br>
  <input type="text" placeholder="Valor gasto" v-model="valor"><br>
  <button @click="adicionar()">+</button>


  <ul>
    <li v-for="ingr in lista" :key="id">{{ ingr.nome }} <button @click="remover(ingr.id)">X</button></li>
  </ul>
{{ lista }}
</template>

<script setup lang="ts">
import { ref } from 'vue';
import type { Item } from '../types/Ingredientes';
const ingrediente = ref<string>();
const quantidade = ref<number>();
const valor = ref<number>(); 
const lista = ref<Item[]>([]);
let id = 0;


function adicionar(){
    if(ingrediente.value === undefined || quantidade.value === undefined || valor.value == undefined ){
        alert('inválido')
        return null
    }
    lista.value.push({
        nome: ingrediente.value,
        quantidade: quantidade.value,
        valor: valor.value,
        id: id++
    });
    ingrediente.value = '';
    valor.value = 0;
    quantidade.value = 0;
}
function remover(ingrediente: string){
    lista.value.splice(lista.value.indexOf(item => item.ingrediente === ingrediente ), 1)
}
</script>

<style>

</style>