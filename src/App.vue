<script setup>
import { reactive } from 'vue';

const estado = reactive({
    calculos: [{
        valor1: 0,
        valor2: 0,
    }
    ]
});

const resultado = () => {
    const { calcular, valor1, valor2 } = estado;

    switch (calcular) {
        case 'somar':
            return (valor1 + valor2)
        case 'subtrair':
            return (valor1 - valor2)
        case 'multiplicar':
            return (valor1 * valor2)
        case 'dividir':
            return (valor1 / valor2)
        default:
            return 0;
    }
}
</script>

<template>
    <div class="container p-5 mb-4 mt-4 bg-dark rounded 3">
        <header>
            <h1>Calculadora</h1>
            <select @change="evento => estado.calcular = evento.target.value" id="">
                <option value="somar">Soma</option>
                <option value="subtrair">Subtração</option>
                <option value="multiplicar">Multiplicação</option>
                <option value="dividir">Divisão</option>
            </select>
        </header>
        <div>
            <input type="number" @keyup="evento => estado.valor1 = parseFloat(evento.target.value)"
                placeholder="Digite um número" id="number1"> <br>
            <input type="number" @keyup="evento => estado.valor2 = parseFloat(evento.target.value)"
                placeholder="Digite um número" id="number2"><br>
        </div>


        <p>Resultado: {{ resultado() }}</p>
    </div>
</template>

<style scoped>
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;

}

h1,
p,
.container {
    text-align: center;
    color: white;
}
</style>
