<script setup lang="ts">
import { reactive, defineProps} from 'vue';

const position = reactive<{ x: number, y: number, scale: number }>({ x: 0, y: 0, scale: 2 });

const props = defineProps<{
    color: string;
    taille: number;
}>();


const updatePosition = (e: MouseEvent) => {
    position.x = e.offsetX;
    position.y = e.offsetY;
    const canvas = document.querySelector('canvas') as HTMLCanvasElement;
    
    const context = canvas.getContext('2d');
    context.beginPath();
    context.fillStyle = props.color;
    context.fillRect(position.x, position.y, props.taille ,props.taille);
    context.closePath();
}
const resetCanvas = () => {
    const canvas = document.querySelector('canvas') as HTMLCanvasElement;
    const context = canvas.getContext('2d');
    context.clearRect(0, 0, canvas.width, canvas.height);
}

</script>


<template>
    <button class="m-auto block mt-2 text-white rounded-lg uppercase font-bold w-2/5 text-center p-2 bg-slate-700" @click="resetCanvas">Reset !</button>
    <canvas @mousemove="updatePosition" width="600" height="400"></canvas>
</template>

<style scoped>
canvas{
    background-color: #eee;
    border: 1px solid #ccc;
    margin: 10px auto;
}

</style>