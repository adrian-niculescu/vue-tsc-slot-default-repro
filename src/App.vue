<script setup lang="ts">
import Child from './Child.vue';
import { KEYS } from './keys';
</script>

<template>
  <Child>
    <template #toolbar="slotProps = {}">{{ slotProps }}</template>
    <template #more>{{ KEYS.MORE }}</template>
  </Child>
</template>
