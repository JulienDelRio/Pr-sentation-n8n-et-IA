<template>
  <div class="slidev-layout layout-default flex flex-col px-12 py-10">
    <div class="flex-1 grid grid-cols-2 gap-10">
      <div class="col-left">
        <slot />
      </div>
      <div class="col-right border-l border-gray-200 pl-10">
        <slot name="right" />
      </div>
    </div>

    <div class="flex items-center justify-between mt-auto pt-4 border-t border-gray-100">
      <span class="text-xs text-gray-400">n8n à l'heure de l'IA</span>
      <span class="text-xs text-gray-300">
        <SlideCurrentNo /> / <SlidesTotal />
      </span>
    </div>
  </div>
</template>
