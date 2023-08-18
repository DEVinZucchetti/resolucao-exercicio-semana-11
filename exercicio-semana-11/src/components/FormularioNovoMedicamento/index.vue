<template>
  <h2>Formulário de Cadastro de medicamentos</h2>
  <div class="d-flex">

    <v-text-field 
      label="Nome" 
      class="w-25 px-2" 
      type="text" 
      variant="outlined" 
      placeholder="Nome do medicamento" 
      v-model="medicamento" 
    />

    <v-text-field label="Laboratório" class="w-25 px-2" type="text" variant="outlined" placeholder="Nome do laboratório" v-model="laboratorio" />

    <v-text-field label="Preço" type="number" class="w-25 px-2" variant="outlined" placeholder="Digite o preço" v-model="preco" />

    <v-btn color="success" class="mt-1 me-2" size="large" @click="$emit('cadastrar', medicamento, laboratorio, preco)">Cadastrar</v-btn>

  </div>
</template>

<script>
export default {
  data(){
    return {
      medicamento: "",
      laboratorio: "",
      preco: 0
    }
  }
}
</script>

<style></style>