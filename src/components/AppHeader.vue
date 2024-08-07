<template>
  <header>
    <div class="header-content" :class="{ shifted: dProps.onMenu }">
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
  </header>
</template>
<script setup lang="ts">
import { defineEmits, defineProps } from 'vue';
const dProps = defineProps({
  onMenu: {
    type: Boolean,
    required: true,
    default: false,
  },
});

const emit = defineEmits(['toggleMenu']);
const toggleMenu = () => {
  emit('toggleMenu');
};
</script>
<style lang="css">
header {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header-content {
  display: flex;
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
  color: #007bff;
}

.shifted {
  margin-left: 220px;
}
</style>
