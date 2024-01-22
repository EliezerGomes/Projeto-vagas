<template>
  <div class="container">
    <div class="row mt-3">
      <div class="col">
        <h4>Apresente a sua vaga para milhares de profissionais de graça!</h4>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Título da vaga</label>
        <input v-model="titulo" type="text" class="form-control" />
        <div class="form-text">
          Por exemplo: Programador JavaScript e Vue.js
        </div>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Descrição</label>
        <textarea
          v-model="descricao"
          type="text"
          class="form-control"
        ></textarea>
        <div class="form-text">Infome os detalhes da vaga</div>
      </div>
    </div>

    <div class="row mt-3">
      <div class="col">
        <label class="form-label">Salário</label>
        <input v-model="salario" type="number" class="form-control" />
        <div class="form-text">Infome o salario</div>
      </div>

      <div class="col">
        <label class="form-label">Modalidade</label>
        <select class="form-select" v-model="modaliade">
          <option value="" disabled>--Selecione--</option>
          <option value="1">Home Office</option>
          <option value="2">Presencial</option>
        </select>
        <div class="form-text">Infome a modalidade</div>
      </div>

      <div class="col">
        <label class="form-label">Tipo</label>
        <select class="form-select" v-model="tipo">
          <option value="" disabled>--Selecione--</option>
          <option value="1">CLT</option>
          <option value="2">PJ</option>
        </select>
        <div class="form-text">Infome o tipo de contratação</div>
      </div>
    </div>

    <div class="row">
      <div class="col">
        <button type="submit" class="btn btn-primary" @click="publicarVaga()">
          Cadastrar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "PublicarVaga",
  setup() {
    const titulo = ref("");
    const descricao = ref("");
    const salario = ref("");
    const modaliade = ref("");
    const tipo = ref("");

    function publicarVaga() {
      let vagas = JSON.parse(localStorage.getItem("vagas"));

      const auxData = new Date(Date.now())
      const dataPublicacao = auxData.toISOString()

      if (!vagas) vagas = [];
      vagas.push({
        titulo: titulo.value,
        descricao: descricao.value,
        salario: salario.value,
        modaliade: modaliade.value,
        tipo: tipo.value,
        publicacao: dataPublicacao
      });

      console.log(vagas);
      localStorage.setItem("vagas", JSON.stringify(vagas));
    }

    return {
      titulo,
      descricao,
      salario,
      modaliade,
      tipo,
      publicarVaga,
    };
  },
};
</script>
