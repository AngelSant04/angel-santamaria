<template>
  <a class="card">
    <img :src="dProps.movie?.img" class="imgCard" alt="" />
    <div class="cardOverlay">
      <div class="cardHeader">
        <div class="cardHeader-text">
          <h3 class="cardTitle">
            {{ dProps.movie?.title + ' ' + dProps.movie?.ageRestriction }}
          </h3>
          <span class="cardGenre">{{ generos }}</span>
        </div>
      </div>
      <p class="cardDescription">
        {{ dProps.movie?.description }}
      </p>
    </div>
  </a>
</template>
<script setup lang="ts">
import { computed, defineProps } from 'vue';
import { Movie } from '@/interface/Movie';

const dProps = defineProps({
  movie: {
    type: Object as () => Movie,
    required: true,
  },
});

const generos = computed(() => {
  return dProps.movie ? dProps.movie.genre.join(' - ') : '';
});
</script>
<style lang="css">
.card {
  position: relative;
  display: block;
  height: 400px;
  width: 100%;
  border-radius: calc(var(--curve) * 1px);
  overflow: hidden;
  text-decoration: none;
  margin: 15px;
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
  gap: 0.25em;
  padding: 1.25em;
  border-radius: calc(var(--curve) * 1px) 0 0 0;
  background-color: var(--surface-color);
  transform: translateY(-100%);
  transition: 0.2s ease-in-out;
}

.card:hover .cardHeader {
  transform: translateY(0);
}

.cardHeader-text {
  text-align: start;
}

.cardTitle {
  font-size: 1em;
  margin: 0 0 0.3em;
  color: #2c2328;
}

.cardGenre {
  font-size: 0.8em;
  color: #363636;
}

.cardDescription {
  padding: 0.25em 2em 2em;
  margin: 0;
  color: #4f4f4f;
  font-family: 'MockFlowFont';
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 3;
  overflow: hidden;
  text-align: start;
}
</style>
