<template>
    <button class="button" @click="clique" :disabled="desabilitado">
            <span class="icon">
                <i class="fas" :class="[ icone ]"></i>
            </span>
            <span>{{ tipo }}</span>
        </button>
</template>

<script lang="ts">

import { defineComponent } from 'vue';

export default defineComponent( {

    name: 'ButtomTemp',
    data () {
        return {
            icone: this.tipo == 'play' ? 'fa-play' : 'fa-stop'
        }
    },
    props: {
        desabilitado: {
            type: Boolean,
            default: false
        },
        tipo: {
            type: String,
            default: 'play'
        }
    },
    emits: [ 'botaoClicado' ],
    methods: {
        clique () : void {
            this.$emit("botaoClicado")
        }
    }
})

</script>