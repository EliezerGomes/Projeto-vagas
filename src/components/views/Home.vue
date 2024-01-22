<template>
    <div class="container py-4">
        <div class="row">
            <div class="col">
                <pesquisar-vaga />
            </div>
        </div>

        <div class="row mt-5" v-for="(vaga, idx) in vagas" :key="idx">
            <div class="col">
                <Vaga v-bind="vaga"/>
            </div>
        </div>

        <div class="row mt-5">
            <div class="col-4">
                <indicador label="Vagas abertas" indicator="25" />
            </div>

            <div class="col-4">
                <indicador label="Profissionais cadastrados" indicator="125" />
            </div>

            <div class="col-4">
                <indicador label="Visitantes online" :indicator="userOnline" background="bg-light" textColor="text-muted" />
            </div>
        </div>
    </div>
</template>

<script>
import PesquisarVaga from "@/components/comuns/PesquisarVaga.vue"
import Indicador from "@/components/comuns/Indicador.vue"
import Vaga from "@/components/comuns/Vaga.vue"
import { onMounted, ref } from "vue"

export default {
    name: "Home",
    components: {
        PesquisarVaga,
        Indicador,
        Vaga
    },
    setup() {
        const userOnline = ref(0)
        let vagas = ref([])
        
        onMounted(() => {
            setInterval(getUserOnline, 3000) // a cada 3 segundos vai ser executado
            const auxVagas = JSON.parse(localStorage.getItem('vagas'))
            if(auxVagas) {
                vagas.value = auxVagas
            }
        })

        function getUserOnline() {
            userOnline.value = Math.floor(Math.random() * 101) //gerando valor entre 0 e 100   
        }

        return { userOnline, vagas }
    }
}
</script>