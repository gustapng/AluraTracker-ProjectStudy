<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <TempoCronometro :tempo-em-segundos="tempoEmSegundos"/>
        <BotaoAcao :texto-botao="'play'" :icone-botao="'fas fa-play'" @click="iniciarContagem" :disabled="cronometroAtivo"/>
        <BotaoAcao :texto-botao="'stop'" :icone-botao="'fas fa-stop'" @click="finalizarContagem" :disabled="!cronometroAtivo"/>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TempoCronometro from './TempoCronometro.vue'
import BotaoAcao from './BotaoAcao.vue'

export default defineComponent({
    name: 'TemporizadorCompleto',
    emits: ['aoTemporizadorFinalizado'],
    components: {
        TempoCronometro,
        BotaoAcao
    },
    data() {
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroAtivo: false,
        }
    },
    methods: {
        iniciarContagem() {
            this.cronometroAtivo = true;
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000)
        },
        finalizarContagem() {
            this.cronometroAtivo = false;
            clearInterval(this.cronometro);
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            this.tempoEmSegundos = 0;
        }
    }
})
</script>