<script setup>
import { reactive } from 'vue';
import Calculadora from './componentes/Calculadora.vue'
const estado = reactive({
  numAnterior:'',
  operador: '',
  numAtual: '',
  resultado: '',

});
const botaoClicado = (texto) =>{
  console.log(texto)
  if(!isNaN(texto)){
    estado.numAtual += toString(texto)
  }else if(texto === 'C') {
  estado.numAnterior= ''
  estado.operador= ''
  estado.numAtual= ''
  estado.resultado= ''
  
}else if(texto === 'DEL'){
  estado.numAnterior = estado.numAnterior.slice(0,-1)
}else{
  if(texto !== ''){
    estado.operador = texto
    estado.numAnterior = estado.numAtual
    estado.numAtual = '';
  }
}
}
</script>

<template>
  <Calculadora :botao-clicado="botaoClicado"
  :resultado="estado.resultado"/>
</template>

