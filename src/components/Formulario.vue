<script setup>
    const props = defineProps(['realizaOperaçao', 'trocarNumeroUm', 'trocarNumeroDois', 'trocarFiltro'])
</script>

<template>
    <form>
      <div class="row justify-content-center">
        <div class="col-md-2">
          <input @keyup="props.trocarNumeroUm" class="form-control" type="number" placeholder="Primeiro número">
        </div>
        <div class="col-md-1 p-0">
          <select @change="props.trocarFiltro" class="form-control botao">
            <option value="default">Operação</option>
            <option value="soma">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">x</option>
            <option value="divisao">/</option>
          </select>
        </div>
        <div class="col-md-2">
          <input @keyup="props.trocarNumeroDois" class="form-control" type="number" placeholder="Segundo número">
        </div>
      </div>
    </form>
</template>

<style scoped>
.form-control {
  max-width: 220px;
  text-align: center;
}
.botao {
  max-width: 100%;
  text-align: center;
}
.resultado {
  font-weight: bold;
}

p {
  font-size: 20px;
}
</style>