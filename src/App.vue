<script setup>
import SplashScreenComponent from '@/components/SplashScreenComponent.vue';
import { defineAsyncComponent } from 'vue';
</script>
<script>
export default {
  components: {
    SplashScreenComponent,
    HomeComponent: defineAsyncComponent(() => {
      return new Promise((resolve) => {
        setTimeout(() => {
          resolve(import('./components/HomeComponent.vue'));
        }, 2500);
      });
    })
  }
};
</script>
<template>
  <Suspense>
    <template #default>
      <HomeComponent />
    </template>
    <template #fallback>
      <SplashScreenComponent />
    </template>
  </Suspense>
</template>

<style scoped>
html,
body,
.app {
  min-height: 100vh;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
}
* {
  --brand-green: #04b500;
  --brand-blue: #0689b0;
}
</style>
