<template>
    <div class="card">
        <div class="card-header bg-dark text-white">
            <div class="row">
                <div class="col d-flex justify-content-between">
                    <div>{{ titulo }}</div>
                    <div>
                        <div class="form-check form-switch">
                            <input class="form-check-input" type="checkbox">
                            <label class="form-check-label">Favoritar</label>
                        </div>
                    </div>
                </div>
            </div>
            <div>

            </div>
        </div>
        <div class="card-body">
            <p>{{ descricao }}</p>
        </div>
        <div class="card-footer">
            <small class="text-muted">Sálario: R$ {{ salario }} | Modalidade: {{ getModalidade }} | Tipo: {{ getTipo }} | Publicação:
                {{ formatData }}
            </small>
        </div>
    </div>
</template>

<script>
import { defineComponent, computed } from 'vue';

export default defineComponent({
    name: "Vaga",
    props: {
        titulo: {
            type: String,
            default: ''
        },
        descricao: {
            type: String,
            default: ''
        },
        salario: {
            type: String,
            default: ''
        },
        modalidade: {
            type: String,
            default: ''
        },
        tipo: {
            type: String,
            default: ''
        },
        publicacao: {
            type: String,
            default: ''
        },
    }, 
    setup(props) {
        const getModalidade = computed(() => {
            switch(props.modalidade) {
                case '1': 
                    return 'Home Office'
                case '2':
                    return 'Presencial'
            }
        })

        const getTipo = computed(() => {
            switch(props.tipo) {
                case '1': 
                    return 'CLT'
                case '2':
                    return 'PJ'
            }
        })

        const formatData = computed(() => {
            const auxFormat = new Date(props.publicacao)
            return auxFormat.toLocaleDateString('pt-BR')
        })

        return { getModalidade, getTipo, formatData }
    }
})
</script>