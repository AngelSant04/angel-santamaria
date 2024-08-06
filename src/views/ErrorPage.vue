<template>
  <div class="container">
    <div>
      <div style="font-size: 30vh">404</div>

      <h2 style="opacity: 0.4">Oops. La ruta no existe</h2>

      <a href="/" class="btn">Go Home</a>
    </div>
  </div>
</template>

<script setup lang="ts"></script>

<style>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: skyblue;
  width: 100vw;
  height: 100vh;
  color: white;
}

.btn {
  display: inline-block;
  padding: 10px 20px;
  margin-top: 1rem;
  background-color: rgb(24, 175, 235);
  color: white;
  border-radius: 4px;
  text-decoration: none;
  font-weight: normal;
  text-transform: none;
  transition: background-color 0.3s, color 0.3s;
  cursor: pointer;
}

.btn:hover {
  background-color: rgb(18, 132, 177);
  color: white;
}

.btn:focus {
  outline: none;
}
</style>
