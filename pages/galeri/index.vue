<template>
  <section
    class="relative min-h-screen flex items-center justify-center
           bg-[#0b0f18] overflow-hidden text-white px-6"
  >

    <!-- RED GLOW BACKGROUND -->
    <div
      class="absolute top-[-150px] left-1/2 -translate-x-1/2
             w-[600px] h-[600px]
             bg-red-600/10 blur-[160px]
             rounded-full pointer-events-none">
    </div>

    <div
      class="absolute bottom-[-100px] right-[-100px]
             w-[400px] h-[400px]
             bg-red-500/5 blur-[140px]
             rounded-full pointer-events-none">
    </div>

    <!-- CARD -->
    <div
      class="relative text-center max-w-xl
             bg-white/5 backdrop-blur-2xl
             border border-white/10
             rounded-3xl p-12
             shadow-[0_20px_60px_rgba(0,0,0,0.6)]"
    >

      <!-- ICON -->
      <div
        class="w-20 h-20 mx-auto mb-8
               rounded-full flex items-center justify-center
               border border-white/10 bg-white/5"
      >
        <svg
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="1.6"
          class="w-10 h-10 text-red-500"
        >
          <circle cx="12" cy="12" r="9"/>
          <line x1="12" y1="7" x2="12" y2="13"/>
          <line x1="12" y1="17" x2="12.01" y2="17"/>
        </svg>
      </div>

      <!-- TITLE -->
      <h1 class="text-3xl md:text-4xl font-bold mb-4">
        Halaman Belum Tersedia
      </h1>

      <!-- DESC -->
      <p class="text-gray-400 leading-relaxed mb-10">
        Fitur ini sedang dalam tahap pengembangan.
        Silakan kembali lagi nanti 🚀
      </p>

      <!-- BUTTON -->
      <NuxtLink
        to="/"
        class="group inline-flex items-center gap-2
               px-8 py-3 rounded-full
               border border-white/15
               bg-white/[0.03]
               backdrop-blur-xl
               transition-all duration-300
               hover:bg-red-500/10
               hover:border-red-500/40
               hover:shadow-[0_0_30px_rgba(239,68,68,0.35)]"
      >
        Kembali ke Beranda
        <span
          class="transition-transform duration-300
                 group-hover:translate-x-1">
          →
        </span>
      </NuxtLink>

    </div>

  </section>
</template>
