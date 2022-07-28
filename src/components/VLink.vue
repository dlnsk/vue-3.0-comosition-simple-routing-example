<template>
  <a
    :href="href"
    @click.prevent="go"
  >
    <slot></slot>
  </a>
</template>

<script setup>
  import emitter from "@/services/emitter";
  import routes from '../routes';

  const props = defineProps({
    href: {
      type:String,
      required: true
    }
  });

  const go = () => {
    window.history.pushState(null, routes[props.href], props.href)
    emitter.emit('routeChanged', props.href);
  }
</script>
