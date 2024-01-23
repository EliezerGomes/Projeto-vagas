<template>
  <div>
    <vagas-favoritas />
    <topo-padrao @navegar="component = $event"/>
    <alerta v-if="alerta"/>
    <Conteudo :component="component"></Conteudo>
  </div>
</template>

<script>
  import "./style/global.css"

  import Conteudo from "@/components/layouts/Conteudo.vue"
  import VagasFavoritas from "@/components/comuns/VagasFavoritas.vue"
  import TopoPadrao from "@/components/layouts/TopoPadrao.vue"
  import Alerta from "@/components/comuns/Alerta.vue"
  import { emitter } from "./main"

  export default {
    name: 'App',
    components: {
      Conteudo,
      TopoPadrao,
      VagasFavoritas, 
      Alerta
    },
    data: () => {
      return {
        component: 'Home',
        alerta: false
      }
    },
    mounted() {
      this.emitter.on('alerta', () => {
        this.alerta = true

        setTimeout(() => {
          this.alerta = false
        }, 3000)
      })

    }
  }
</script>
