<template>
  <div class="slidev-layout layout-end flex flex-col items-center justify-center text-center px-16 py-12">
    <img
      src="https://juliendelrio.fr/wp-content/uploads/2025/10/logo_jdr_2025_transp_sans_marge-300x300.png"
      alt="JDR Logo"
      class="w-20 h-20 rounded-full shadow-xl mb-8"
    />

    <slot />

    <div class="flex gap-6 mt-8">
      <a href="https://twitter.com/juliendelrio" target="_blank" class="flex items-center gap-2 text-sm text-white/60 hover:text-white transition-colors">
        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        @juliendelrio
      </a>
      <a href="https://www.linkedin.com/in/juliendelrio/" target="_blank" class="flex items-center gap-2 text-sm text-white/60 hover:text-white transition-colors">
        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        juliendelrio
      </a>
      <a href="https://juliendelrio.fr" target="_blank" class="flex items-center gap-2 text-sm text-white/60 hover:text-white transition-colors">
        <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9.004 9.004 0 008.716-6.747M12 21a9.004 9.004 0 01-8.716-6.747M12 21c2.485 0 4.5-4.03 4.5-9S14.485 3 12 3m0 18c-2.485 0-4.5-4.03-4.5-9S9.515 3 12 3m0 0a8.997 8.997 0 017.843 4.582M12 3a8.997 8.997 0 00-7.843 4.582m15.686 0A11.953 11.953 0 0112 10.5c-2.998 0-5.74-1.1-7.843-2.918m15.686 0A8.959 8.959 0 0121 12c0 .778-.099 1.533-.284 2.253m0 0A17.919 17.919 0 0112 16.5a17.92 17.92 0 01-8.716-2.247m0 0A8.966 8.966 0 013 12c0-1.97.633-3.794 1.706-5.274"/></svg>
        juliendelrio.fr
      </a>
    </div>

    <div class="mt-10 text-xs text-white/30">
      <slot name="footer">
        Factory Tech — Digital 113 — 18 février 2026
      </slot>
    </div>
  </div>
</template>
