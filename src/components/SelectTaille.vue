<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';
import { TailleInterface } from '../../shared/interfaces/TailleInterface';

const props = defineProps<{
    taille: number;
    color: string;
}>()

const emit = defineEmits<{
    (e :"changeTaille", taille: number) : void
}>()

const listTaille: TailleInterface[] =
    [
        {
            name: 'Petit',
            taille: 4
        },
        {
            name: 'Moyen',
            taille: 7
        },
        {
            name: 'Grand',
            taille: 14
        }
    ];



</script>

<template>
    <div class=" w-1/2 m-auto">
        <div class="grid grid-cols-3 text-center gap-2 mt-4">
            <div class="p-2 border border-gray-600 rounded-lg cursor-pointer" :class="{'bg-slate-500' : taille.taille === props.taille}" v-for="taille in listTaille" :key="taille.name" @click="emit('changeTaille', taille.taille)">{{ taille.name }}</div>
        </div>
    </div>
</template>

<style scoped>
.cube {
    width: 20px;
    height: 20px;
}


</style>