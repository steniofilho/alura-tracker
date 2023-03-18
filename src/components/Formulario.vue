<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa deseja iniciar?" v-model="descricao" />
            </div>
            <div class="column">
                <TemporizadorForm @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import TemporizadorForm from '@/components/TemporizadorForm.vue';
export default defineComponent({
    name: 'FormularioPrincipal',
    components: {
        TemporizadorForm
    },
    data () {
        return {
            // essa propriedade foi ligada ao input de tarefa via v-model
            descricao: ''
        }
    },
    methods: {
        // o metodo abaixo é invocado quando o emit do componente Temporizador é chamado
        finalizarTarefa(tempoDecorrido: number) : void {
            // o emit emite evento e joga os valores na interface ITarefa
            this.$emit('aoSalvarTarefa',{
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao = ''
            
        }
    },
    emits: [ 'aoSalvarTarefa']
})

</script>

<style>
.formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);

}
</style>