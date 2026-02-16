<template>
  <div class="slidev-layout layout-cover flex flex-col justify-center px-16 py-12">
    <div class="flex-1 flex flex-col justify-center">
      <slot />
    </div>

    <div class="flex items-center gap-6 mt-auto pt-8 border-t border-white/15">
      <slot name="footer">
        <p class="text-sm text-white/50">Factory Tech — Digital 113</p>
      </slot>
    </div>
  </div>
</template>
