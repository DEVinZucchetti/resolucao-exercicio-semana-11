<!--
  PASSOS PARA CRIAR UM COMPONENTE:
  - 1 [x] - crie um arquivo dentro da pasta components
  - 2 [x] - dê o nome ao arquivo usando PascalCase
    Obs: PascalCase significa que as primeiras letras de cada palavra
    sempre serão maiúsculas.
  - 3 [x] - Escreva a estrutura base do arquivo Vue (Single File Component
  - template | script | style)
  - 4* [x] - Se for usar props, defina o array de props
    - 4.1* - [x] Defina onde as props devem ser utilizadas
    - 5 [x] - importe o componente no local que será utilizado
    import NomeDoComponente from "./components/NomeDoComponente.vue"
  - 6 [x] - Registre o componente na propriedade components:
    components: { // esse fica dentro do export default
      NomeDoComponente
    }
    6.1 [] - Adicione o componente no template no arquivo onde ele foi importado
  - 7* [] - Se usou props, passe os valores das props para serem utilizados
-->

<template>
  <div class="card">
    <button @click="$emit('favoritar', id)">Favoritar</button>
    <span v-if="favorito">Favorito</span>
    <img :width="120" src="https://dmvfarma.vtexassets.com/arquivos/ids/196865/caixa-medicamento-2021.png?v=637695586068000000" alt="Imagem do medicamento" />
    <span>Nome: {{ nome }}</span>
    <span>Laboratório: {{ laboratorio }}</span>
    <span>Preço: {{ preco }}</span>
  </div>
</template>
<script>
export default {
  props: ['nome', 'laboratorio', 'preco', 'favorito', 'id']
}
</script>
<style scoped>
.card {
  display: flex;
  flex-direction: column;
  width: calc(100%/4 - 2em);
  margin: 1em;
  background-color: #C4C4C4;
}
  
</style>