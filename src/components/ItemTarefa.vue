<template>
    <BoxConteudo>
        <div class="columns">
            <div class="column is-7">
                <p>{{ tarefa.descricao || 'Tarefa sem descrição' }}</p>
            </div>
            <div class="column">
                <TempoCronometro :tempo-em-segundos="tarefa.duracaoEmSegundos"/>
            </div>
        </div>
    </BoxConteudo>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import TempoCronometro from './TempoCronometro.vue';
import BoxConteudo from './BoxConteudo.vue';
import ITarefa from '@/interfaces/ITarefa';

export default defineComponent({
    name: 'ItemTarefa',
    data() {
        return {
            tempoEmSegundos: 0,
        }
    },
    components: {
        TempoCronometro,
        BoxConteudo
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>

<style scoped>

</style>