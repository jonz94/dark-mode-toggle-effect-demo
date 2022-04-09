<script setup lang="ts">
defineProps({
  command: String,
})
</script>

<template>
  <div class="overflow-hidden rounded border p-4">
    <pre class="overflow-auto">{{ command }}</pre>
  </div>
</template>
