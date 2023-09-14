<script setup>
import { reactive } from 'vue';
import Calculadora from './componentes/Calculadora.vue'
const estado = reactive({
  numAnterior:'',
  operador: ['+','-','X','/'],
  operadorAtual: '',
  numAtual: '',
  resultado: '',

});
const botaoClicado = (texto) =>{
    if(texto >= '0' && texto <= '9' ){
      estado.numAtual += texto
    }
    else if(texto === 'C') {
    estado.numAnterior= ''
    estado.operador= ''
    estado.numAtual= ''
    estado.resultado= ''
    
    }
    else if(texto === 'DEL'){
      estado.numAnterior = estado.numAnterior.slice(0,-1)
    }
    else if(texto === '.'){
      if (this.estado.numAtual.indexOf('.') === -1) {
        this.append('.');
      }else{
        return
      }

    }
    else if(estado.operador.includes(texto)){
      estado.operadorAtual = texto 
    }
    else{
    if(texto === '='){
        calcular()
        estado.operadorAtual= ''
    }

    estado.numAnterior= estado.numAtual
    estado.numAtual= ''
  }
}


const calcular  = () => {
  const {operadorAtual} = estado
  const num1 = parseFloat(estado.numAtual)
  const num2 = parseFloat(estado.numAnterior)
  switch(operadorAtual){
    case '+': {
      estado.resultado = (num1 + num2).toString
      break;
    }
    case '-': {
      estado.resultado = (num1 - num2).toString
      break;
    }
    case '/': {
      estado.resultado = (num1 / num2).toString
      break;
    }
    case 'X': {
      estado.resultado = (num1 / num2).toString
      break;
    }
  }
  return estado.resultado 
}
</script>

<template>
  <Calculadora :botao-clicado="botaoClicado"
  :resultado="estado.resultado"
  />
</template>

