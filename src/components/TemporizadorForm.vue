<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <CronometroForm :tempoEmSegundos="tempoEmSegundos" />
        <ButtonTemp @botaoClicado="iniciar" :desabilitado=cronometroRodando tipo='play' />
        <ButtonTemp @botaoClicado="finalizar" :desabilitado=!cronometroRodando tipo='stop' />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroForm from "@/components/CronometroForm.vue"
import ButtonTemp from "@/components/ButtonTemp.vue"

export default defineComponent({
    name: 'TemporizadorForm',
    components: {
        CronometroForm, ButtonTemp
    },
    emits: [ 'aoTemporizadorFinalizado'],
    data () {
        return {
            tempoEmSegundos: 0, // esse valor é passado como parametro v-bind para CronometroForm
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciar () {
            // começar a contagem
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempoEmSegundos += 1;
            }, 1000)
        },
        finalizar () {
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('aoTemporizadorFinalizado',this.tempoEmSegundos)
            this.tempoEmSegundos = 0
        }
    }
})
</script>