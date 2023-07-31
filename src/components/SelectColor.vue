<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

const props = defineProps<{
    color: string
}>()

const emit = defineEmits<{
    (e: "changeColor", color: string): void
}>()

const colorPalette: string[] =
    ['#6d001a', '#be0039', '#ff4500', '#ffa800', '#ffd635', '#fff8b8',
        '#00a368', '#00cc78', '#7eed56', '#00756f', '#009eaa', '#00ccc0',
        '#2450a4', '#3690ea', '#51e9f4', '#493ac1', '#6a5cff', '#94b3ff',
        '#811e9f', '#b44ac0', '#e4abff', '#de107f', '#ff3881', '#ff99aa',
        '#6d482f', '#9c6926', '#ffb470', '#000000', '#515252', '#898d90',
        '#d4d7d9', '#ffffff'];

</script>

<template>
    <div class="flex gap-2">
        <div v-for="color in colorPalette" :key="color" class="w-6 h-6" :style="{ backgroundColor: color }"
            :class="{ 'w-8 h-8': color === props.color }" @click="emit('changeColor', color)"></div>
    </div>
</template>

<style scoped>
.cube {
    width: 20px;
    height: 20px;
}
</style>