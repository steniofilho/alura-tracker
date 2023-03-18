<template>
    <section>
        <strong class="display">{{ tempoDecorrido }}</strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent( {
    name: 'CronometroForm',
    props: {
        tempoEmSegundos: {
            type: Number,
            default: 0
        }
    },
    computed: {
        // monitora propriedades e executa quando é atualizado
        tempoDecorrido () : string {
            return new Date(this.tempoEmSegundos * 1000).toISOString().substring(11,19)
        }
    },
})
</script>

<style>
.display {
    color: var(--texto-primario);

}
</style>