<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="descricao">
            </div>
            <div class="column">
                <TemporizadorCompleto @ao-temporizador-finalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TemporizadorCompleto from './TemporizadorCompleto.vue'

export default defineComponent({
    name: 'FormularioTarefa',
    emits: ['aoSalvarTarefa'],
    components: {
        TemporizadorCompleto
    },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number) : void {
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao = '';
        }
    }
})
</script>

<style>
    .formulario {
        color: var(--texto-primario);
        background-color: var(--bg-primario);
    }
</style>