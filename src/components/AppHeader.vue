<template>
  <header>
    <div class="header-content">
      <button class="menu-button">
        <font-awesome-icon :icon="['fas', 'bars']" />
      </button>
      <div class="header-title">Prueba Técnica Angel Santamaría</div>
    </div>
  </header>
</template>
<script setup lang="ts"></script>
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
}

.header-title {
  font-size: 1.2rem;
  font-weight: bold;
  display: flex;
  align-items: center;
  margin-left: 0.5rem;
}

.menu-button {
  background-color: transparent;
  color: white;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
  font-size: 1.2rem;
  cursor: pointer;
  transition: background-color 0.3s;
}

.menu-button:hover {
  background-color: #e7e7e7;
  color: #007bff;
}
</style>
