<template>
  <section class="relative py-20 bg-[#0b0f18] overflow-hidden">

    <div class="max-w-7xl mx-auto px-6 md:px-20">

      <h2 class="text-center text-3xl md:text-4xl font-bold text-white mb-14">
        Dokumentasi <span class="text-red-500">Kegiatan</span>
      </h2>

      <!-- Gradient Fade -->
      <div class="fade-left"></div>
      <div class="fade-right"></div>

      <!-- ROW ATAS -->
      <div class="carousel-wrapper">
        <div class="carousel-track animate-left">
          <div
            v-for="(img, i) in duplicatedImages"
            :key="'top-' + i"
            class="carousel-item"
          >
            <img :src="img" />
          </div>
        </div>
      </div>

      <!-- ROW BAWAH -->
      <div class="carousel-wrapper mt-8">
        <div class="carousel-track animate-right">
          <div
            v-for="(img, i) in duplicatedImages"
            :key="'bottom-' + i"
            class="carousel-item"
          >
            <img :src="img" />
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
const images = [
  "/images/foto1.jpg",
  "/images/foto2.jpg",
  "/images/foto3.jpg",
  "/images/foto4.jpg",
  "/images/foto5.jpg",
]

const duplicatedImages = [...images, ...images]
</script>

<style scoped>
.carousel-wrapper {
  overflow: hidden;
  width: 100%;
}

.carousel-track {
  display: flex;
  gap: 16px;
  width: max-content;
}

/* ITEM */
.carousel-item {
  width: 260px;
  height: 170px;
  flex-shrink: 0;
  border-radius: 18px;
  overflow: hidden;
  border: 1px solid rgba(255,255,255,0.08);
  transition: all 0.4s ease;
}

.carousel-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.carousel-item:hover {
  transform: scale(1.07);
}

/* ANIMATION */
@keyframes scrollLeft {
  from { transform: translateX(-50%); }
  to { transform: translateX(0); }
}

@keyframes scrollRight {
  from { transform: translateX(0); }
  to { transform: translateX(-50%); }
}

.animate-left {
  animation: scrollLeft 35s linear infinite;
}

.animate-right {
  animation: scrollRight 35s linear infinite;
}

/* Pause hover */
.carousel-wrapper:hover .carousel-track {
  animation-play-state: paused;
}

/* Fade Edges */
.fade-left,
.fade-right {
  position: absolute;
  top: 0;
  width: 120px;
  height: 100%;
  z-index: 10;
  pointer-events: none;
}

.fade-left {
  left: 0;
  background: linear-gradient(to right, #0b0f18 0%, transparent 100%);
}

.fade-right {
  right: 0;
  background: linear-gradient(to left, #0b0f18 0%, transparent 100%);
}
</style>
