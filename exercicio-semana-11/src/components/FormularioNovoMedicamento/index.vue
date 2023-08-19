<template>
  <h2>Formulário de Cadastro de medicamentos</h2>
  <v-form ref="form" class="d-flex">

    <v-text-field 
      label="Nome" 
      class="w-25 px-2" 
      type="text" 
      variant="outlined" 
      placeholder="Nome do medicamento" 
      v-model="medicamento" 
      :rules="[v => !!v || 'O nome é obrigatório!']"
      required
    />

    <v-text-field 
    label="Laboratório" 
    class="w-25 px-2" type="text" 
    variant="outlined" 
    placeholder="Nome do laboratório" 
    v-model="laboratorio" 
    :rules="[v => !!v || 'O nome do laboratório é obrigatório!']"
    required
    />

    <v-text-field 
      label="Preço" 
      type="number" 
      class="w-25 px-2" 
      variant="outlined" 
      placeholder="Digite o preço" 
      v-model="preco" 
      :rules="[v => !!v || 'O preço é obrigatório!']"
      required
    />

    <v-btn color="success" class="mt-1 me-2" size="large" @click="AdicionarMedicamento">Cadastrar</v-btn>

  </v-form>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
import axios from 'axios'
export default {
  data(){
    return {
      medicamento: "",
      laboratorio: "",
      preco: 0
    }
  },
  methods: {
    async AdicionarMedicamento() {
      const {valid} = await this.$refs.form.validate()

      if(!valid){
        return
      }

      const novoMedicamento = {
        id: uuidv4(),
        nome: this.medicamento,
        laboratorio: this.laboratorio,
        preco: this.preco,
        favorito: false
      }

      try {
        await axios.post('http://localhost:50001/medicamentos', novoMedicamento)
      } catch (erro) {
        console.log(erro)
      }
    },
  }
}
</script>

<style></style>