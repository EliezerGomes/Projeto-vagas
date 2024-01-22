<template>
  <div>
    <div class="div-flutuante">
      <button
        class="btn btn-primary"
        type="button"
        data-bs-toggle="offcanvas"
        data-bs-target="#offcanvasRight"
        aria-controls="offcanvasRight"
      >
        Vagas favoritas
      </button>
    </div>

    <div
      class="offcanvas offcanvas-end"
      tabindex="-1"
      id="offcanvasRight"
      aria-labelledby="offcanvasRightLabel"
    >
      <div class="offcanvas-header">
        <h5 class="offcanvas-title" id="offcanvasRightLabel">
          Vagas favoritadas
        </h5>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="offcanvas"
          aria-label="Close"
        ></button>
      </div>
      <div class="offcanvas-body">
        <ul class="list-group" v-if="vagas.length > 0">
          <li class="list-group-item" v-for="(vaga, index) in vagas" :key="index">
            {{ vaga }}
          </li>
        </ul>

        <span v-else>Nenhuma vaga favoritada!</span>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent, onMounted, ref } from "vue";
import { emitter } from "@/main";

export default defineComponent({
  name: "VagasFavoritas",
  setup() {
    const vagas = ref([])

    onMounted(() => {
      emitter.on("favoritarVaga", (titulo) => {
        vagas.value.push(titulo)
      })
      emitter.on("desfavoritarVaga", (titulo) => {
        let indice = vagas.value.indexOf(titulo)
        if (indice !== -1) vagas.value.splice(indice, 1)
      })
    })

    return { vagas }
  },
});
</script>

<style scoped>
.div-flutuante {
  position: absolute;
  z-index: 1;
  top: 70px;
  right: 10px;
}
</style>
