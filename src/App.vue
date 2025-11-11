<template>
  <TheNav />
  <div class="app-container">
    <GoBack />
    <router-view v-slot="{ Component }">
      <component :is="Component" :key="$route.path"></component>
    </router-view>
  </div>
</template>

<script>
import TheNav from '@/components/TheNav.vue';
import GoBack from '@/components/GoBack.vue';
export default {
  components: { TheNav, GoBack }
}
</script>