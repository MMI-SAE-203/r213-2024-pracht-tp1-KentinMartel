<script setup lang="ts">
import { ref } from 'vue';

const maVar = ref(true)
</script>

<template>
  <button @click="maVar = false">cache</button>
  <br> 
  <button @click="maVar = true">pas cache</button>

  <h1 v-show="maVar" class="text-2xl">Bonjour monde !</h1>
</template>
