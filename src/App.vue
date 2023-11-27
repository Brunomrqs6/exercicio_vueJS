<script setup>
  import { reactive } from 'vue';
  import Cabecalho from './components/Cabeçalho.vue'
  import Formulario from './components/Formulario.vue'

  const estado = reactive ({
    numero1: 0,
    numero2: 0,
    filtro: '',
  })

  const soma = () => {
    const soma1 = parseFloat(estado.numero1) + parseFloat(estado.numero2)
    return soma1.toFixed(2)
  }

  const subtrai = () => {
    const subtrai1 = parseFloat(estado.numero1) - parseFloat(estado.numero2)
    return subtrai1.toFixed(2)
  }

  const multiplica = () => {
    const multiplica1 = parseFloat(estado.numero1) * parseFloat(estado.numero2)
    return multiplica1.toFixed(2)
  }

  const divide = () => {
    const divide1 = parseFloat(estado.numero1) / parseFloat(estado.numero2)
    return divide1.toFixed(2)
  }

  const realizaOperaçao = () => {
    const { filtro } = estado;

    switch (filtro) {
      case 'soma':
        return soma();
      case 'subtracao':
        return subtrai();
      case 'multiplicacao':
        return multiplica();
      case 'divisao':
        return divide();
    }
  }
</script>

<template>
  <div class="container text-center">
    <Cabecalho />
    <Formulario :realiza-operaçao = "realizaOperaçao()" :trocar-numero-um = "evento => estado.numero1 = evento.target.value" :trocar-numero-dois = "evento => estado.numero2 = evento.target.value" :trocar-filtro = "evento => estado.filtro = evento.target.value" />
    <p class="mt-3" v-if="estado.filtro != 'default' & estado.numero1 != '' & estado.numero2 != ''">O resultado foi <span class="resultado">{{ realizaOperaçao() }}</span></p>
  </div>
</template>

<style>
.resultado {
  font-weight: bold;
}

p {
  font-size: 20px;
}
</style>


