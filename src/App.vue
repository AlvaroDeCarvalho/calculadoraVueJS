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
  console.log(estado.resultado)
  console.log(estado.numAtual)
  console.log(estado.numAnterior)
  const textoInteiro = parseInt(texto)
  if(textoInteiro >= 0 && texto <= 9){
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
    if (estado.numAtual.indexOf('.') === -1) {
      estado.numAtual.append('.');
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

function calcularOperacao() {
  if (estado.numAnterior  && estado.operadorAtual  && estado.numAtual) {
    return `${estado.numAnterior} ${estado.operadorAtual} ${estado.numAtual}`;
  } else {
    return '';
  }
}

const calcular = () => {
  const { operadorAtual } = estado;
  const num1 = parseFloat(estado.numAnterior);
  const num2 = parseFloat(estado.numAtual);

  if (isNaN(num1) || isNaN(num2) || !operadorAtual) {
    estado.resultado = ''; // Caso não haja números ou operador válido, definir resultado como vazio
  } else {
    switch (operadorAtual) {
      case '+':
        estado.resultado = (num1 + num2).toString();
        break;
      case '-':
        estado.resultado = (num1 - num2).toString();
        break;
      case '/':
        estado.resultado = (num1 / num2).toString();
        break;
      case 'X':
        estado.resultado = (num1 * num2).toString();
        break;
      default:
        estado.resultado = ''; // Operador inválido, definir resultado como vazio
    }
  }
  estado.numAtual = ''; // Limpar numAtual após o cálculo
  estado.numAnterior = ''; // Limpar numAnterior após o cálculo
  estado.operadorAtual = ''; // Limpar operadorAtual após o cálculo
  return estado.resultado;
}
</script>

<template>
  <Calculadora :botao-clicado="botaoClicado"
  :mostrar-result="calcularOperacao()"
  />
</template>

