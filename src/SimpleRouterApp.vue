<script setup>
  import { computed, onMounted, ref, defineAsyncComponent } from 'vue';
  import emitter from "@/services/emitter";
  import routes from "./routes";

  const currentRoute = ref(window.location.pathname);

  const ViewComponent = computed(() => {
    const matchingPage = routes[currentRoute.value] || '404';
    return defineAsyncComponent(() => import(`./pages/${matchingPage}.vue`));
  });

  emitter.on(
    'routeChanged',
    e => currentRoute.value = e
  );

  onMounted(() => {
    window.addEventListener('popstate', () => {
      currentRoute.value = window.location.pathname;
    });
  });
</script>


<template>
  <component :is="ViewComponent"></component>
</template>
