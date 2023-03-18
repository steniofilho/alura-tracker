<template>
    <div class="box hat-text-weight-bold" :style="estilos">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'BoxItem',
    data () {
        return {
            estilos: {
                background: '#FAF0CA'
            }
        }
    }
})
</script>