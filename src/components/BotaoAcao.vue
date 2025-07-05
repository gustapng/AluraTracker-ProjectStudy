<template>
    <button class="button">
        <span class="icon">
            <i :class="iconeBotao"></i>
        </span>
        <span>{{ textoBotao }}</span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'BotaoAcao',
    props: {
        textoBotao: {
            type: String,
            default: ''
        },
        iconeBotao: {
            type: String,
            default: ''
        }
    },
})
</script>