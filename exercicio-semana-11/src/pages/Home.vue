<template>
  <router-link to="/novo-medicamento">+ medicamento</router-link>
  <div>
    <CardMedicamento 
      v-for="medicamento in listaMedicamentos" 
      :key="medicamento.id" 
      @favoritar="FavoritarMedicamento"
      :nome="medicamento.nome" 
      :laboratorio="medicamento.laboratorio" 
      :preco="medicamento.preco" 
      :id="medicamento.id" 
    />
  </div>
</template>

<script>
import CardMedicamento from "../components/CardMedicamento/index.vue"
export default {
  components: {
    CardMedicamento
  },
  data() {
    return {
      listaMedicamentos: [
        {
          id: 1,
          nome: 'Dorflex',
          laboratorio: 'Clamed',
          preco: 2,
          favorito: false
        }
      ]
    }
  },
  methods: {
    FavoritarMedicamento(id) {
      // editar o medicamento e marcar como favorito
      this.listaMedicamentos = this.listaMedicamentos.map(item => {
        if(item.id == id){
          item.favorito = !item.favorito
        }

        return item
      })
    }
  }
}
</script>