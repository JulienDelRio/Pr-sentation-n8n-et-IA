<template>
  <div class="slidev-layout layout-cover flex flex-col justify-center px-16 py-12">
    <div class="flex items-center gap-5 mb-10">
      <img
        src="https://juliendelrio.fr/wp-content/uploads/2025/10/logo_jdr_2025_transp_sans_marge-300x300.png"
        alt="JDR Logo"
        class="w-16 h-16 rounded-full shadow-lg"
      />
      <div class="h-10 w-px bg-white/30" />
      <span class="text-white/60 text-sm font-medium tracking-wide uppercase">Julien Del Rio</span>
    </div>

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
