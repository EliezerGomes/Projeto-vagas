<template>
  <div>
    <vagas-favoritas />
    <topo-padrao @navegar="component = $event"/>
    <Conteudo :component="component"></Conteudo>
  </div>
</template>

<script>
  import "./style/global.css"

  import Conteudo from "@/components/layouts/Conteudo.vue"
  import VagasFavoritas from "@/components/comuns/VagasFavoritas.vue"
  import TopoPadrao from "@/components/layouts/TopoPadrao.vue"

  export default {
    name: 'App',
    components: {
      Conteudo,
      TopoPadrao,
      VagasFavoritas
    },
    data: () => {
      return {
        component: 'Home',
      }
    }
  }
</script>
