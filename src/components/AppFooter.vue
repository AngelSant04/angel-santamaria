<template lang="">
  <footer class="footer_area">
    <div class="footer_social">
      <a
        target="_blank"
        href="https://www.facebook.com/profile.php?id=100002130923168"
      >
        <font-awesome-icon class="icon" :icon="['fab', 'facebook']" />
        <!-- <i class="fa-brands fa-facebook"></i> -->
      </a>
      <a target="_blank" href="https://www.instagram.com/angel_santamaria04/">
        <font-awesome-icon class="icon" :icon="['fab', 'instagram']" />
        <!-- <i class="fa fa-instagram"></i> -->
      </a>
      <a
        target="_blank"
        href="https://www.linkedin.com/in/angel-santamaria-herrera-392657244/"
      >
        <!-- <i class="fa fa-linkedin"></i> -->
        <font-awesome-icon class="icon" :icon="['fab', 'linkedin']" />
      </a>
      <a target="_blank" href="https://github.com/AngelSant04">
        <!-- <i class="fa fa-github"></i> -->
        <font-awesome-icon class="icon" :icon="['fab', 'github']" />
      </a>
    </div>
    <div class="row footer_bottom">
      <p class="footer-text">
        Copyright &copy;
        {{ dProps.year }}
        Todos los derechos reservados
      </p>
    </div>
  </footer>
</template>
<script setup lang="ts">
import { defineProps } from 'vue';
const dProps = defineProps({
  year: {
    type: Number,
    required: true,
  },
});
</script>
<style>
.footer_area {
  padding: 40px 0;
  position: relative;
}

.footer_area:before {
  content: '';
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  background: #3498db12;
  z-index: -1;
}

.footer_area .footer_social {
  text-align: center;
  margin: 30px 0px;
}

.footer_area .footer_social a {
  padding: 0 20px;
}

.footer_area .footer_social a .icon {
  color: #788489;
  font-size: 22px;
  -webkit-transition: all 0.4s ease 0s;
  -moz-transition: all 0.4s ease 0s;
  -o-transition: all 0.4s ease 0s;
  transition: all 0.4s ease 0s;
}

.footer_area .footer_social a .icon:hover {
  color: #3498db;
}

.footer_area .footer_bottom {
  text-align: center;
  justify-content: center;
}

.footer_area .footer_bottom a {
  color: #3498db;
}
</style>
