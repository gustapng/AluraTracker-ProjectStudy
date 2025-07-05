<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral />
    </div>
    <div class="column is-three-quarter">
      <FormularioTarefa @ao-salvar-tarefa="salvarTarefa"/>
      <div class="lista">
        <ItemTarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxConteudo v-if="listaEstaVazia">
          <p>Você não está muito produtivo hoje :(</p>
        </BoxConteudo>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue'
import FormularioTarefa from './components/FormularioTarefa.vue'
import ItemTarefa from './components/ItemTarefa.vue';
import BoxConteudo from './components/BoxConteudo.vue';
import ITarefa from './interfaces/ITarefa';

export default defineComponent({
  name: 'App',
  components: { BarraLateral,
    FormularioTarefa,
    ItemTarefa,
    BoxConteudo
  },
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia() : boolean {
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    }
  }
});
</script>

<style>
  .lista {
    padding: 1.25rem;
  }
</style>
