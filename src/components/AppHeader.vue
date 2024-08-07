<template>
  <header>
    <div
      class="header-content flex justify-between"
      :class="{ shifted: dProps.onMenu }"
    >
      <div class="flex">
        <button class="menu-button" @click="toggleMenu">
          <font-awesome-icon :icon="['fas', 'bars']" />
        </button>
        <a
          href="https://angelsant04.github.io/angel-dev/"
          class="header-title"
          target="_blank"
        >
          Angel Dev
        </a>
      </div>
      <div class="flex justify-center align-center" style="margin-right: 40px">
        <input
          type="color"
          id="colorPicker"
          class="color-picker"
          @input="changeColor"
        />
      </div>
    </div>
  </header>
</template>
<script setup lang="ts">
import { defineEmits, defineProps, onMounted } from 'vue';

const dProps = defineProps({
  onMenu: {
    type: Boolean,
    required: true,
    default: false,
  },
});
const emit = defineEmits(['toggleMenu']);

const updateColor = (color: any) => {
  document.documentElement.style.setProperty('--primary-color', color);
  localStorage.setItem('mainColor', color);
};

const changeColor = (event: Event) => {
  const input = event.target as HTMLInputElement;
  updateColor(input.value);
};

const toggleMenu = () => {
  emit('toggleMenu');
};

onMounted(() => {
  const savedColor = localStorage.getItem('mainColor');
  if (savedColor) {
    document.documentElement.style.setProperty('--primary-color', savedColor);
    const colorPicker = document.querySelector(
      '#colorPicker'
    ) as HTMLInputElement;
    if (colorPicker) {
      colorPicker.value = savedColor;
    }
  }
});
</script>
<style lang="css">
header {
  background-color: var(--primary-color);
  color: white;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-content {
  width: 100%;
  transition: margin-left 0.3s ease;
}

.header-title {
  font-size: 1.2rem;
  font-weight: bold;
  display: flex;
  align-items: center;
  margin-left: 0.5rem;
  text-decoration: none;
  color: inherit;
}

.menu-button {
  background-color: transparent;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
  margin: 0;
  font-size: 1.2rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.menu-button:hover {
  background-color: #e7e7e7;
  color: var(--primary-color);
}

.shifted {
  margin-left: 220px;
}
</style>
