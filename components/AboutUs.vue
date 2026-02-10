<template>
  <section class="relative bg-[#0b0b0f] text-white pt-32 pb-28 overflow-hidden">

    <!-- TOP SHADOW TRANSITION -->
     <!-- Smooth Blend Top -->
    <div class="absolute top-0 left-0 w-full h-40 bg-gradient-to-b from-black/80 via-black to-[#0b0b0f] pointer-events-none"></div>

    <!-- Background Glow Accent -->
    <div class="absolute top-20 -left-40 w-[500px] h-[500px] bg-red-500/10 blur-[150px] rounded-full"></div>
    <div class="absolute bottom-0 right-0 w-[400px] h-[400px] bg-purple-500/10 blur-[150px] rounded-full"></div>

    <div class="relative max-w-7xl mx-auto px-6 md:px-20">

      <!-- Heading -->
      <div class="text-center mb-20">
        <h1 class="text-4xl md:text-5xl font-bold mb-6">
          Tentang <span class="text-red-500">Kami</span>
        </h1>
        <p class="text-gray-400 max-w-2xl mx-auto">
          SOS 25 adalah sekumpulan agen perubahan yang kreativ & inovatif,
          Yang menjung-jung tinggi akan perkembangan Intelektual.
        </p>
      </div>

      <!-- Content -->
      <div class="grid md:grid-cols-2 gap-16 items-center">

        <!-- IMAGE -->
        <div class="relative group">

          <!-- Glow -->
          <div class="absolute inset-0 bg-red-500/20 blur-2xl opacity-30 group-hover:opacity-50 transition"></div>

          <img
            src="/images/colab.png"
            class="relative rounded-3xl shadow-2xl border border-white/10 w-full object-cover"
          />

        </div>

        <!-- TEXT -->
        <div>

          <h2 class="text-2xl md:text-3xl font-semibold mb-6">
            Siapa Kami?
          </h2>

          <p class="text-gray-400 leading-relaxed mb-6">
            Kami adalah tim dokumentasi dan media kreatif yang bertugas
            mengabadikan momen penting serta membangun citra organisasi
            melalui visual dan konten digital.
          </p>

          <p class="text-gray-400 leading-relaxed mb-10">
            Dengan semangat kolaborasi dan inovasi, kami menghadirkan
            pengalaman digital yang modern dan profesional.
          </p>

          <!-- Stats -->
          <div class="grid grid-cols-3 gap-6">

            <div class="bg-white/5 backdrop-blur-xl p-6 rounded-2xl border border-white/10 text-center">
              <h3 class="text-3xl font-bold text-red-500">36+</h3>
              <p class="text-gray-400 text-sm mt-2">Anggota Aktif</p>
            </div>

            <div class="bg-white/5 backdrop-blur-xl p-6 rounded-2xl border border-white/10 text-center">
              <h3 class="text-3xl font-bold text-red-500">10+</h3>
              <p class="text-gray-400 text-sm mt-2">Event</p>
            </div>

            <div class="bg-white/5 backdrop-blur-xl p-6 rounded-2xl border border-white/10 text-center">
              <h3 class="text-3xl font-bold text-red-500">100+</h3>
              <p class="text-gray-400 text-sm mt-2">Dokumentasi</p>
            </div>

          </div>

        </div>

      </div>

    </div>

  </section>
</template>
