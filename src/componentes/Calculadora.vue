<script setup>
    const props = defineProps(['botaoClicado','mostrarResult',])
</script>


<template>
    <div class="container">
        <div class="calculadora">
        <h1>Calculadora</h1>
         <p id="resultado">{{ props.mostrarResult }}</p>
        <table>
            <tr>
                <td><button class="botao" @click="props.botaoClicado('C')"  >C</button></td>
                <td><button class="botao" @click="props.botaoClicado('DEL')"  >DEL </button></td>
                <td><button class="botao" @click="props.botaoClicado('/')"  >/</button></td>
                <td><button class="botao" @click="props.botaoClicado('X')"  >X</button></td>
            </tr>
            <tr>
                <td><button class="botao" @click="props.botaoClicado('7')"  >7</button></td>
                <td><button class="botao" @click="props.botaoClicado('8')"  >8</button></td>
                <td><button class="botao" @click="props.botaoClicado('9')"  >9</button></td>
                <td><button class="botao" @click="props.botaoClicado('-')"  >-</button></td>
            </tr>
            <tr>
                <td><button class="botao" @click="props.botaoClicado('4')"  >4</button></td>
                <td><button class="botao" @click="props.botaoClicado('5')"  >5</button></td>
                <td><button class="botao" @click="props.botaoClicado('6')"  >6</button></td>
                <td><button class="botao" @click="props.botaoClicado('+')"  >+</button></td>
            </tr>
            <tr>
                <td><button class="botao" @click="props.botaoClicado('1')"  >1</button></td>
                <td><button class="botao" @click="props.botaoClicado('2')"  >2</button></td>
                <td><button class="botao" @click="props.botaoClicado('3')"  >3</button></td>
                <td rowspan="2"> <button class="botao" style="height: 106px;" @click="botaoClicado('=') ">=</button></td>
            </tr>
            <tr>
                <td colspan="2"><button class="botao" style="width: 106px;" @click="props.botaoClicado(0)">0</button></td>
                <td><button class="botao" @click="props.botaoClicado('.')">.</button></td>
            </tr>
        </table>
    </div>
    </div>
</template>

<style scoped>

        *{
            margin: 0;
            padding: 0;
            font-family: sans-serif;
        }
        .container{
            background-image: linear-gradient(45deg,rgb(176, 186, 24), crimson);
            height: 100vh;
            color: #fff;
            font-family: Arial, Helvetica, sans-serif;
            text-align: center;
        }
        .calculadora{
            position: absolute;
            background-color: rgba(0, 0, 0, 0.8);
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
            border-radius: 15px;
            padding: 15px;
        }
        .botao{
            width: 50px;
            height: 50px;
            font-size: 25px;
            cursor: pointer;
            margin: 3px;
            background-color: rgb(31,31,31);
            border: none;
            color: #fff;
        }
        .botao:hover{
            background-color: black;
        }
        #resultado{
            background-color: white;
            width: 207px;
            height: 30px;
            margin: 5px;
            font-size: 25px;
            color: black;
            text-align: right;
            padding: 5px;
        }
</style>
