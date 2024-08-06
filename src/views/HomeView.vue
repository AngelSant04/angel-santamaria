<template>
  <div>
    <AppHeader></AppHeader>
    <main>
      <div class="container">
        <div v-for="element in movies" :key="element.id">
          <CardMovie :movie="element"></CardMovie>
        </div>
      </div>
    </main>
    <AppFooter></AppFooter>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import axios from 'axios';
import { Movie } from '@/interface/Movie';
import AppHeader from '@/components/AppHeader.vue';
import AppFooter from '@/components/AppFooter.vue';
import CardMovie from '@/components/CardMovie.vue';

const year: any = ref(null);
const movies = ref<Movie[]>([]);

const loadMovies = async () => {
  try {
    const response = await axios.get('/Movies.json');
    // console.log(response);
    movies.value = response.data.movies;
  } catch (error) {
    console.error('Error:', error);
  }
};

onMounted(async () => {
  const date = new Date();
  year.value = date.getFullYear();
  await loadMovies();
});
</script>
<style scoped>
main {
  width: 100%;
}

.container {
  padding: 50px;
}
</style>
