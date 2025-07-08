<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @ao-tema-alterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
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
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
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
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
  .lista {
    padding: 1.25rem;
  }

  .main {
    --bg-primario: #FFF;
    --texto-primario: #000;
  }

  main.modo-escuro {
    --bg-primario: #2B2D42;
    --texto-primario: #DDD;
  }

  .conteudo {
    background-color: var(--bg-primario);
  }
</style>
