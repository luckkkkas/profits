<template>
  <h1>listagem</h1>
  <input type="text" placeholder="Ingrediente" v-model="ingrediente"><br>
  <input type="number" placeholder="quantidade usado  (em g)" v-model="quantidadeUsada"><br>
  <input type="number" placeholder="quantidade do produto (em g ou unidades)" v-model="quantidadeProduto"><br>
  <input type="text" placeholder="Valor gasto" v-model="valor"><br>
  <button @click="adicionar()">+</button>
  
  
  <div >
    <ul>
      <li  v-for="ingr in lista" v-bind:key="ingr.id">{{ ingr.nome }} <button @click="remover(ingr)">X</button></li>
    </ul>
  </div>
  <div>
    <table v-if="lista[0]">
      <tr>
        <th>Ingrediente</th>
        <th>usado</th>
        <th>Despesas (R$)</th>
        <th>Qnt. comprada</th>
      </tr>
      <tr  v-for="ingr in lista" :key="ingr.id">
        <td>{{ ingr.nome }}</td>
        <td>{{ ingr.quantidade }}</td>
        <td>{{ ingr.valor }}</td>
        <td>{{ ingr.produto }}</td>
      </tr>
    </table>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import type { Item } from '../types/Ingredientes';
const ingrediente = ref<string>();
const quantidadeUsada = ref<number>();
const quantidadeProduto = ref<number>();
const valor = ref<number>(); 
const lista = ref<Item[]>([]);
let id = 0;


function adicionar(){
    if(ingrediente.value === undefined || quantidadeUsada.value === undefined || valor.value == undefined || quantidadeProduto.value == undefined){
        alert('inválido')
        return null
    }

    lista.value.push({
        nome: ingrediente.value,
        quantidade: quantidadeUsada.value,
        produto: quantidadeProduto.value,
        valor: Math.round(somar()),
        id: id++
    });
    ingrediente.value = '';
    valor.value = 0;
    quantidadeUsada.value = 0;
    quantidadeProduto.value = 0;
  }
function somar (){
    const prorporcao = valor.value / quantidadeProduto.value;
    return prorporcao;
}
function remover(ingr: any){
    lista.value.splice(lista.value.findIndex(ingrediente => ingrediente.id === ingr.id ), 1)
}
</script>

<style>

</style>