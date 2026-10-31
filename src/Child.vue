<script setup lang="ts">
defineSlots<{ toolbar(props: { item: string }): unknown; more(): unknown }>();
</script>

<template>
  <slot name="toolbar" item="a" />
  <slot name="more" />
</template>
