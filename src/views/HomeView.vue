<template>
  <div>
    <AppHeader :onMenu="menuVisible" @toggleMenu="toggleMenu"></AppHeader>
    <aside :class="{ 'menu-visible': menuVisible }">
      <h2 style="color: white; margin: 12px 20px">Filtros</h2>
      <hr class="filter-separetor" />
      <div class="filter-section">
        <div class="select-box" :class="{ active: showOptions }">
          <div class="select-option" @click="showOptions = !showOptions">
            <input type="text" id="optionSearch" placeholder="Search" name="" />
          </div>
          <div class="content">
            <div class="search">
              <input
                type="text"
                id="optionSearch"
                placeholder="Search"
                name=""
              />
            </div>
            <ul class="options">
              <li>HTML</li>
              <li>CSS</li>
            </ul>
          </div>
        </div>
        <!-- <label for="genres" class="filter-label">Géneros:</label>
        <select
          id="genres"
          class="filter-select"
          v-model="genreSelected"
          multiple
        >
          <option value="all">Todos</option>
          <option v-for="genre in arrGenre" :key="genre" :value="genre">
            {{ genre }}
          </option>
        </select> -->
      </div>
      <div class="filter-section">
        <label for="description" class="filter-label">Descripción:</label>
        <textarea
          id="description"
          class="filter-text-area"
          placeholder="Descripción"
          rows="5"
          v-model="description"
        />
      </div>
      <div class="filter-section flex justify-end">
        <button class="filter-button" @click="searchMovies">Buscar</button>
      </div>
    </aside>
    <main :class="{ shifted: menuVisible }">
      <div class="row">
        <div class="col flex justify-end">
          <input type="text" placeholder="Nombre" v-model="name" />
        </div>
        <div
          v-for="element in filteredMovies"
          :key="element.id"
          class="col col-lg-4 col-md-4 col-sm-6 col-xs-12 flex justify-center align-center"
        >
          <CardMovie :movie="element"></CardMovie>
        </div>
      </div>
    </main>
    <AppFooter :year="year" :class="{ shifted: menuVisible }"></AppFooter>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref, computed } from 'vue';
import axios from 'axios';
import { Movie } from '@/interface/Movie';
import AppHeader from '@/components/AppHeader.vue';
import AppFooter from '@/components/AppFooter.vue';
import CardMovie from '@/components/CardMovie.vue';

const year = ref<number>(0);
const movies = ref<Movie[]>([]);
const moviesOriginal = ref<Movie[]>([]);
const name = ref('');
const genreSelected = ref<string[]>(['all']);
const description = ref('');
const menuVisible = ref(false);
const arrGenre: any = ref(null);

const showOptions = ref(false);

const filteredMovies = computed(() => {
  return movies.value.filter((e: Movie) =>
    e.title.toLowerCase().includes(name.value.toLowerCase())
  );
});

const searchMovies = () => {
  if (description.value === '' && genreSelected.value.length === 0) {
    movies.value = [...moviesOriginal.value];
  } else {
    let filteredMovies =
      genreSelected.value.length === 0 || genreSelected.value.includes('all')
        ? [...moviesOriginal.value]
        : moviesOriginal.value.filter((e: Movie) =>
            e.genre.some((g: string) => genreSelected.value.includes(g))
          );

    if (description.value !== '') {
      filteredMovies = filteredMovies.filter((movie: Movie) =>
        movie.description
          .toLowerCase()
          .includes(description.value.toLowerCase())
      );
    }
    movies.value = filteredMovies;
  }

  toggleMenu();
};

const toggleMenu = () => {
  menuVisible.value = !menuVisible.value;
};

const loadGenres = async () => {
  const setGenres = new Set();
  movies.value.forEach((movie: Movie) => {
    movie.genre.forEach((g) => setGenres.add(g));
  });
  arrGenre.value = Array.from(setGenres);
};

const loadMovies = async () => {
  try {
    const response = await axios.get('/Movies.json');
    movies.value = response.data.movies;
    moviesOriginal.value = response.data.movies;
  } catch (error) {
    console.error('Error:', error);
  }
};

onMounted(async () => {
  const date = new Date();
  year.value = date.getFullYear();
  await loadMovies();
  await loadGenres();
});
</script>
<style scoped>
.row input[type='text'] {
  border: none;
  border-bottom: 1px solid #333;
  padding: 8px 12px;
  margin: 20px;
  outline: none;
  box-shadow: none;
  font-size: 16px;
  background-color: #f9f9f9;
  transition: border-color 0.3s;
  width: 33.33%;
}

.row input[type='text']:focus {
  border-bottom: 2px solid #007bff;
}

aside {
  position: fixed;
  top: 0;
  left: -220px;
  width: 220px;
  height: 100%;
  background-color: #007bff;
  transition: left 0.3s ease;
  z-index: 2;
}

.menu-visible {
  /* margin-left: 220px; */
  left: 0;
}

main {
  transition: margin-left 0.3s ease;
}

AppFooter {
  transition: margin-left 0.3s ease;
}

.filter-separetor {
  border: none;
  border-bottom: 1px solid white;
  margin-bottom: 20px;
}

.filter-section {
  margin-bottom: 15px;
  margin-left: 10px;
  margin-right: 10px;
}

.filter-label {
  display: block;
  margin: 5px 0px;
  font-size: 1rem;
  text-align: start;
  color: white;
}

.select-box {
  width: 100%;
}

.select-option {
  position: relative;
}

.select-option input {
  width: 100%;
  background-color: white;
  color: #000;
  border-radius: 7px;
  cursor: pointer;
  font-size: 22px;
  border: 0 !important;
  outline: 0 !important;
}

.select-option::after {
  content: '';
  border-top: 12px solid #000;
  border-left: 8px solid transparent;
  border-right: 8px solid transparent;
  position: absolute;
  right: 15px;
  top: 50%;
  margin-top: -8px;
}

.content {
  background-color: white;
  position: absolute;
  color: #000;
  border-radius: 7px;
  margin-top: 15px;
  width: 100%;
  z-index: 999;
  padding: 20px;
  display: none;
}

.search input {
  width: 100%;
  font-size: 17px;
  padding: 15px;
  outline: 0;
  border: 1px solid #b3b3b3;
  border-radius: 5px;
}

.options {
  margin-top: 10px;
  max-height: 250px;
  overflow-y: auto;
  padding: 0;
}

.options li {
  padding: 10px 15px;
  border-radius: 5px;
  font-size: 21px;
  cursor: pointer;
  border-bottom: 1px solid gray;
}

.options li:hover {
  background-color: #f2f2f2;
}

.select-box.active .content {
  display: block;
}

.filter-select,
.filter-text-area {
  width: 100%;
  padding: 8px;
  border: 1px solid #007bff;
  border-radius: 4px;
  background-color: white;
  color: black;
}

.filter-text-area {
  width: 90%;
  resize: none;
}

.filter-select:focus,
.filter-text-area:focus {
  outline: none;
  border-color: #007bff;
}

.filter-button {
  background-color: white;
  color: black;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  font-size: 1rem;
  cursor: pointer;
  position: absolute;
  right: 10px;
  bottom: 20px;
}
</style>
