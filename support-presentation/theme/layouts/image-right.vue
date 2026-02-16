<template>
  <div class="slidev-layout layout-default flex h-full">
    <div class="flex-1 flex flex-col justify-center px-12 py-10">
      <slot />
    </div>
    <div
      class="w-2/5 bg-cover bg-center"
      :style="{ backgroundImage: `url(${$attrs.image || ''})` }"
    />
  </div>
</template>

<script setup>
defineProps({
  image: String,
})
</script>
