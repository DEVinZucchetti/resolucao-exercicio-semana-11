<template>
  <div>
    <FormularioNovoMedicamento @cadastrar="AdicionarMedicamento" />
  </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
import FormularioNovoMedicamento from "../components/FormularioNovoMedicamento/index.vue"
export default {
  components: {
    FormularioNovoMedicamento
  },
  methods: {
    AdicionarMedicamento(nome, laboratorio, preco) {

      if (nome == "" || laboratorio == "" || preco == 0) {
        alert("Preencha todos os dados")
        return
      }

      const novoMedicamento = {
        id: uuidv4(),
        nome: nome,
        laboratorio: laboratorio,
        preco: preco,
        favorito: false
      }

      // TODO
      this.listaMedicamentos.push(novoMedicamento)
    },
  }
}
</script>