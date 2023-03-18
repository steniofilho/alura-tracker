<template>
    <BoxItem>

        <div class="columns">
            <div class="column is-7">
                {{ tarefa_item.descricao || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <CronometroForm :tempoEmSegundos="tarefa_item.duracaoEmSegundos" />
            </div>
        </div>

    </BoxItem>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import CronometroForm from './CronometroForm.vue';
import ITarefa from '@/interfaces/ITarefa'
import BoxItem from './BoxItem.vue';
export default defineComponent({
    name: 'TarefaItem',
    components: {
        CronometroForm, BoxItem
    },
    props: {
        tarefa_item: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>

<!-- scoped indica só neste componente-->
<style scoped>

</style>