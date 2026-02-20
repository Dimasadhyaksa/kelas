<template>
  <section class="relative py-20 bg-[#0b0f18] overflow-hidden">

    <div class="max-w-7xl mx-auto px-6 md:px-20">

      <h2 class="text-center text-3xl md:text-4xl font-bold text-white mb-14">
        Dokumentasi <span class="text-red-500">Kegiatan</span>
      </h2>

      <!-- Fade Edge -->
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
            <img :src="img" loading="lazy" />
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
            <img :src="img" loading="lazy" />
          </div>
        </div>
      </div>
    </div>
    <!-- BUTTON -->
<div class="flex justify-center mt-14">
  <NuxtLink
    to="/galeri"
    class="group relative px-10 py-3 rounded-full
           border border-white/15
           bg-white/[0.03]
           backdrop-blur-xl
           text-white tracking-wide
           transition-all duration-300
           hover:bg-red-500/10
           hover:border-red-500/40
           hover:shadow-[0_0_30px_rgba(239,68,68,0.35)]"
  >
    <span class="relative z-10 flex items-center gap-2">
      Selengkapnya
      <span
        class="transition-transform duration-300 group-hover:translate-x-1"
      >
        →
      </span>
    </span>

    <!-- glow layer -->
    <div
      class="absolute inset-0 rounded-full opacity-0
             group-hover:opacity-100
             bg-gradient-to-r
             from-transparent via-red-500/20 to-transparent
             blur-xl transition duration-500">
    </div>
  </NuxtLink>
</div>

  </section>
</template>

<script setup>
import { ref, computed, onMounted } from "vue"
import { createClient } from "@supabase/supabase-js"

const config = useRuntimeConfig()

const supabase = createClient(
  config.public.supabaseUrl,
  config.public.supabaseAnonKey
)

const images = ref([])

/* ======================
   FETCH DATA SUPABASE
====================== */
const fetchImages = async () => {
  const { data, error } = await supabase
    .from("images") // ✅ NAMA TABLE KAMU
    .select("image") // ✅ KOLOM IMAGE
    .order("id", { ascending: true })

  if (error) {
    console.error("Fetch images error:", error)
    return
  }

  // ambil hanya URL gambar
  images.value = data.map(item => item.image)
}

onMounted(fetchImages)

/* ======================
   DUPLICATE FOR LOOP
====================== */
const duplicatedImages = computed(() => [
  ...images.value,
  ...images.value
])
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

/* animation */
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

.carousel-wrapper:hover .carousel-track {
  animation-play-state: paused;
}

/* fade */
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
