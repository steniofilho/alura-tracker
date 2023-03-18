<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="alterarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioPrincipal @aoSalvarTarefa="salvarTarefa" />
      <div class="lista">
        <BoxItem v-if="listaVazia">
         Você não tem nenhuma tarefa registrada
        </BoxItem>
        <TarefaItem v-for="(tarefa,index) in tarefas" :key="index" :tarefa_item="tarefa"/> 
      </div>
      
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from '@/components/BarraLateral.vue';
import FormularioPrincipal from "@/components/Formulario.vue";
import TarefaItem from './components/TarefaItem.vue';
import ITarefa from "@/interfaces/ITarefa"
import BoxItem from './components/BoxItem.vue';
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioPrincipal,
    TarefaItem,
    BoxItem
},
  data () {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    } 
  },
  computed: {
    listaVazia () : boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa (tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    alterarTema (modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
    padding: 1.25rem;
}
main {
  --bg-primario: #ffffff;
  --texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
