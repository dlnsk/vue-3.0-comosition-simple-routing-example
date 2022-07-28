<template>
  <ul>
    <li><v-link href="/">Home</v-link></li>
    <li><v-link href="/about">About</v-link></li>
    <li><v-link href="/foo">Under Construction</v-link></li>
  </ul>

  <slot></slot>
</template>

<script setup>
import VLink from '../components/VLink.vue'

</script>
