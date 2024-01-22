<template>
    <div class="h-100 p-5 bg-light border rounded-3">
        <h2>Pesquisar vagas</h2>
        <div class="row">
            <div class="col">
                <div class="form-group">
                    <label>Título da vaga</label>
                    <input type="text" class="form-control" placeholder="Pesquise por palavras chaves">
                    <small class="form-text text-muted">Informe palavras que estejam relacionadas com o titulo
                        da vaga que você procura</small>
                </div>
            </div>
        </div>

        <div class="row">
            <div class="col">
                <button class="btn btn-outline-dark mt-2" type="button">Buscar</button>
            </div>
        </div>
    </div>
</template>

<script>
import { defineComponent } from "vue"
export default defineComponent({
    name: "PesquisarVaga"
})
</script>