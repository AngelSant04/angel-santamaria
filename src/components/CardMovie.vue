<template>
  <a href="" class="card">
    <img :src="dProps.movie?.img" class="imgCard" alt="" />
    <div class="cardOverlay">
      <div class="cardHeader">
        <div class="cardHeader-text">
          <h3 class="cardTitle">Jessica Parker</h3>
          <span class="cardRestrict">1 hour ago</span>
        </div>
      </div>
      <p class="cardDescription">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Asperiores,
        blanditiis?
      </p>
    </div>
  </a>
</template>
<script setup lang="ts">
import { defineProps } from 'vue';
import { Movie } from '@/interface/Movie';

const dProps = defineProps<{
  movie: Movie | null;
}>();
</script>
<style lang="css">
.card {
  position: relative;
  display: block;
  height: 350px;
  width: 350px;
  border-radius: calc(var(--curve) * 1px);
  overflow: hidden;
  text-decoration: none;
}

/* Overflow: hidden -> Oculta Cualquier Contenido Fuera del Contenedor */

.imgCard {
  width: 100%;
  height: auto;
}

.cardOverlay {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 1;
  border-radius: calc(var(--curve) * 1px);
  background-color: var(--surface-color);
  transform: translateY(100%);
  transition: 0.2s ease-in-out;
}

.card:hover .cardOverlay {
  transform: translateY(0);
}

.cardHeader {
  position: relative;
  display: flex;
  align-items: center;
  gap: 2em;
  padding: 2em;
  border-radius: calc(var(--curve) * 1px) 0 0 0;
  background-color: var(--surface-color);
  transform: translateY(-100%);
  transition: 0.2s ease-in-out;
}

.card:hover .cardHeader {
  transform: translateY(0);
}

.cardTitle {
  font-size: 1em;
  margin: 0 0 0.3em;
  color: #6a515e;
}

.cardRestrict {
  font-size: 0.8em;
  color: #d7bdca;
}

.cardDescription {
  padding: 0 2em 2em;
  margin: 0;
  color: #d7bdca;
  font-family: 'MockFlowFont';
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
}
</style>
