<template>
  <div>
    <TheNavigation />

    <div class="container">
      <router-view v-slot="{ Component }">
        <transition name="slide" mode="out-in">
          <component :is="Component" :key="$route.path"></component>
        </transition>
      </router-view>
    </div>
  </div>
</template>

<script>
import { RouterView } from 'vue-router';
import TheNavigation from './components/TheNavigation.vue';

export default {
  components: {
    RouterView,
    TheNavigation
  },
};
</script>

<style lang="css">
.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.3s, transform 1s;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateX(-30%);
}

.component-with-image img {
  width: 100%;
  /* Resim genişliği 100% */
  height: 100%;
  /* Resim yüksekliği 100% */
  object-fit: cover;
  /* Resmin tamamen kaplamasını sağlar */
}</style>
