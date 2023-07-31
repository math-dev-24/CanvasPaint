<script setup lang="ts">
import SelectColor from './components/SelectColor.vue';
import CanvasPlace from './components/CanvasPlace.vue';
import SelectTaille from './components/SelectTaille.vue';
import { reactive } from 'vue';


const state = reactive<{
  color : string;
  taille: number;

}>({
  color: '#ffa800',
  taille: 2

})
const changeColor = (color: string) => {
  state.color = color;
}
const changeTaille = (taille: number) => {
  state.taille = taille;
}
</script>

<template>
  <CanvasPlace :color="state.color" :taille="state.taille"/>
  <SelectColor :color="state.color" @change-color="changeColor" />
  <SelectTaille :color="state.color" :taille="state.taille" @change-taille="changeTaille" />

</template>

