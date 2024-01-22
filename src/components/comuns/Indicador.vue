<template>
    <div :class="estilo">
        <p> {{ label }} </p>
        <h2> {{ indicator }} </h2>
    </div>
</template>

<script>
import { defineComponent, computed } from "vue"
export default defineComponent({
    name: "Indicador",
    props: {
        label: {
            type: String,
            default: ""
        },
        indicator: {
            type: String,
            default: ""
        },
        background: {
            type: String,
            default: 'bg-dark'
        },
        textColor: {
            type: String,
            default: 'text-white'
        }
    },
    setup (props) {
        const estilo = computed(() => {
            return `h-100 p-5 rounded-3 border ${props.background} ${props.textColor}`
        })

        return { estilo }
    }    
})
</script>