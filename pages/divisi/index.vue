<script setup>
const divisions = [
  {
    name: "Divisi IT",
    icon: "💻",
    desc: "Mengelola website, database, dan sistem digital kelas.",
    members: 5,
    color: "hover:border-blue-500/40 hover:shadow-blue-500/20"
  },
  {
    name: "Dokumentasi",
    icon: "📸",
    desc: "Bertanggung jawab atas foto dan video kegiatan kelas.",
    members: 6,
    color: "hover:border-purple-500/40 hover:shadow-purple-500/20"
  },
  {
    name: "Event",
    icon: "🎉",
    desc: "Merancang dan menjalankan acara kelas.",
    members: 7,
    color: "hover:border-orange-500/40 hover:shadow-orange-500/20"
  },
  {
    name: "Publikasi",
    icon: "📢",
    desc: "Mengelola media sosial dan informasi kelas.",
    members: 4,
    color: "hover:border-pink-500/40 hover:shadow-pink-500/20"
  },
  {
    name: "Keuangan",
    icon: "💰",
    desc: "Mengatur kas dan laporan keuangan kelas.",
    members: 3,
    color: "hover:border-green-500/40 hover:shadow-green-500/20"
  }
]
</script>

<template>
<section class="min-h-screen bg-[#0b0f18] text-white">

  <!-- ================= HERO ================= -->
  <div class="relative py-28 text-center overflow-hidden">

    <!-- glow -->
    <div class="absolute -top-40 left-1/2 -translate-x-1/2
                w-[600px] h-[600px]
                bg-red-600/10 blur-[160px]
                rounded-full pointer-events-none" />

    <h1 class="text-4xl md:text-6xl font-bold relative z-10">
      Struktur <span class="text-red-500">Divisi</span>
    </h1>

    <p class="text-gray-400 mt-6 max-w-2xl mx-auto relative z-10">
      Setiap anggota memiliki peran untuk membangun kelas yang aktif,
      kreatif, dan terorganisir.
    </p>

  </div>

  <!-- ================= STATS ================= -->
  <div class="max-w-6xl mx-auto px-6 grid grid-cols-1 md:grid-cols-3 gap-6 mb-20">

    <div class="stat-card">
      <h3>5</h3>
      <p>Total Divisi</p>
    </div>

    <div class="stat-card">
      <h3>36</h3>
      <p>Total Anggota</p>
    </div>

    <div class="stat-card">
      <h3>12+</h3>
      <p>Kegiatan</p>
    </div>

  </div>

  <!-- ================= DIVISION GRID ================= -->
  <div class="max-w-7xl mx-auto px-6 md:px-20 pb-28">

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-8">

      <div
        v-for="(div, i) in divisions"
        :key="i"
        class="group bg-white/5 backdrop-blur-xl
               border border-white/10
               rounded-3xl p-8
               transition-all duration-300
               hover:-translate-y-2
               hover:shadow-2xl"
        :class="div.color"
      >

        <!-- ICON -->
        <div class="text-4xl mb-6">
          {{ div.icon }}
        </div>

        <!-- TITLE -->
        <h2 class="text-xl font-semibold mb-3">
          {{ div.name }}
        </h2>

        <!-- DESC -->
        <p class="text-gray-400 text-sm leading-relaxed">
          {{ div.desc }}
        </p>

        <!-- MEMBER -->
        <p class="mt-6 text-sm text-gray-300">
          {{ div.members }} Anggota
        </p>

        <!-- BUTTON -->
        <NuxtLink
          to="/coming-soon"
          class="inline-flex items-center gap-2 mt-6
                 text-red-400 hover:text-red-300
                 transition"
        >
          Lihat Tim →
        </NuxtLink>

      </div>

    </div>

  </div>

  <!-- ================= CTA ================= -->
  <div class="relative text-center py-20 border-t border-white/5">

    <div class="absolute inset-0
                bg-gradient-to-r
                from-transparent via-red-500/5 to-transparent" />

    <h2 class="text-3xl font-semibold relative z-10">
      Bangun Kelas Bersama 🚀
    </h2>

    <p class="text-gray-400 mt-4 relative z-10">
      Kolaborasi membuat kita lebih kuat.
    </p>

    <NuxtLink
      to="/"
      class="inline-block mt-8 px-8 py-3 rounded-full
             bg-red-600 hover:bg-red-500
             transition shadow-lg shadow-red-600/30"
    >
      Kembali ke Beranda
    </NuxtLink>

  </div>

</section>
</template>

<style scoped>

/* ===== STAT CARD ===== */
.stat-card {
  @apply bg-white/5 backdrop-blur-xl border border-white/10
         rounded-2xl p-8 text-center transition;
}

.stat-card h3 {
  @apply text-3xl font-bold text-red-500;
}

.stat-card p {
  @apply text-gray-400 mt-2 text-sm;
}

</style>
