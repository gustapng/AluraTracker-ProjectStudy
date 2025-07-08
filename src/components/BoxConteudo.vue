<template>
    <div class="box has-text-weight-bol" :style="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent ({
    name: 'BoxConteudo',
    data() {
        return {
            estilos: {
                background: '#FAF0CA'
            }
        }
    }
})
</script>