<script setup>
const images = [
  '/images/foto1.jpg',
  '/images/foto2.jpg',
  '/images/foto3.jpg'
]

// bikin banyak biar penuh
const bgImages = Array(40).fill(images).flat()
</script>

<template>
  <section class="relative w-full min-h-screen overflow-hidden text-white">

    <!-- BACKGROUND -->
    <div class="absolute inset-0 overflow-hidden">

      <div class="mosaic animate-slide">

        <div
          v-for="(img, i) in bgImages"
          :key="i"
          class="mosaic-item"
          :style="{ backgroundImage: `url(${img})` }"
        ></div>

      </div>

      <!-- Dark Layer -->
      <div class="absolute inset-0 bg-black/70"></div>

    </div>

    <!-- Gradient -->
    <div class="absolute inset-0 bg-gradient-to-r from-black/90 via-red-900/60 to-black/95"></div>

    <!-- CONTENT -->
    <div class="relative z-10 max-w-7xl mx-auto px-6 md:px-20 py-32 flex flex-col md:flex-row items-center justify-between gap-12">

      <!-- TEXT -->
      <div class="max-w-xl">
        <p class="uppercase tracking-widest text-gray-300 text-sm">
          SELAMAT DATANG DI
        </p>

        <h1 class="text-5xl md:text-7xl font-extrabold mt-4">
          SHADLE OR STUGGEL <span class="text-red-500">25</span>
        </h1>

        <p class="mt-6 text-gray-300">
          Website dokumentasi dan informasi kegiatan kami.
        </p>

        <button class="mt-8 bg-red-600 hover:bg-red-700 transition px-8 py-3 rounded-full">
          Selengkapnya →
        </button>
      </div>

      <!-- POLAROID -->
      <div class="transform rotate-6 hover:rotate-0 hover:scale-105 transition duration-500">
        <div class="bg-white p-4 rounded-xl shadow-2xl">
          <img
            src="/images/foto2.jpg"
            class="w-60 md:w-72 object-cover rounded-md"
          />
        </div>
      </div>

    </div>

  </section>
  <AboutUs/>
  <ImageCarousel/>

</template>

<style scoped>

/* MOSAIC GRID */
.mosaic {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  gap: 20px;
  width: 200%;
  transform: rotate(-10deg) scale(1.3);
}

.mosaic-item {
  height: 180px;
  background-size: cover;
  background-position: center;
  border-radius: 20px;
  opacity: 0.3;
}

/* HORIZONTAL MOVE */
@keyframes slide {
  0% {
    transform: translateX(0) rotate(-10deg) scale(1.3);
  }
  100% {
    transform: translateX(-50%) rotate(-10deg) scale(1.3);
  }
}

.animate-slide {
  animation: slide 35s linear infinite;
}

</style>
