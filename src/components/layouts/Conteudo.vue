<template>
    <div>
        <component :is="component"/>
    </div>
</template>

<script>
import { ref } from "vue"
import Home from "@/components/views/Home.vue"
import PublicarVaga from "@/components/views/PublicarVaga.vue"

export default {
    name: "Conteudo",
    props: {
        component: {
            type: String,
            default: 'Home'
        }
    },
    components: {
        Home, 
        PublicarVaga
    }
}
</script>