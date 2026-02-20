<script setup>
import { ref, onMounted } from "vue"
import { createClient } from "@supabase/supabase-js"

const container = ref(null)
const members = ref([])
const loading = ref(true)

const config = useRuntimeConfig()

const supabase = createClient(
  config.public.supabaseUrl,
  config.public.supabaseAnonKey
)

// Ambil public image URL dari storage
const getImageUrl = (filename) => {
  if (!filename) return ""

  const { data } = supabase
    .storage
    .from("images") // nama bucket
    .getPublicUrl(`members/${filename}`)

  return data.publicUrl
}

onMounted(async () => {
  const { data, error } = await supabase
    .from("member")
    .select("*")
    .order("id", { ascending: true })

  if (error) {
    console.error("Error ambil member:", error)
  } else {
    members.value = data
    console.log("Data member:", data)
  }

  loading.value = false

  if (container.value) {
    container.value.scrollLeft =
      container.value.scrollWidth / 4
  }
})
</script>

<template>
  <section class="py-28 bg-[#0b0f18] text-white">
    <div class="max-w-7xl mx-auto px-6">

      <h2 class="text-center text-3xl md:text-4xl font-bold mb-16">
        Tim <span class="text-red-500">Kami</span>
      </h2>

      <div v-if="loading" class="text-center text-gray-400">
        Loading...
      </div>

      <!-- SLIDER -->
      <div
        v-else
        ref="container"
        class="flex gap-8 overflow-x-auto scroll-smooth snap-x snap-mandatory no-scrollbar"
      >

        <div
          v-for="member in members"
          :key="member.id"
          class="snap-center shrink-0 w-[280px] md:w-[320px] transition-all duration-500 group"
        >

          <div
            class="bg-white/5 backdrop-blur-xl border border-white/10 
                   rounded-3xl p-6 shadow-xl transition-all duration-300"
          >

            <!-- IMAGE -->
            <div class="relative rounded-2xl overflow-hidden mb-6 group">

               <img
                :src="member.images"
                alt="member"
                class="w-full h-[260px] object-cover
                       transition-all duration-500 ease-out
                       grayscale blur-sm brightness-75
                       group-hover:grayscale-0
                       group-hover:blur-0
                       group-hover:brightness-100"
              />

              <!-- Overlay -->
              <div
                class="absolute inset-0 bg-black/40
                       transition-opacity duration-500
                       group-hover:opacity-0"
              ></div>

              <!-- Nama Tengah -->
              <div
                class="absolute inset-0 flex items-center justify-center
                       transition-opacity duration-500
                       group-hover:opacity-0"
              >
                <h3 class="text-white text-xl font-semibold tracking-wide">
                  {{ member.name }}
                </h3>
              </div>

            </div>

            <!-- TEXT -->
            <h3 class="text-lg font-semibold text-center">
              {{ member.role }}
            </h3>

            <p class="text-gray-400 text-center mt-2 text-sm">
              {{ member.skill }}
            </p>

            <!-- SOCIAL -->
           <div class="flex justify-center gap-6 mt-6 text-gray-400">

  <!-- Instagram -->
  <a
    :href="member.ig"
    target="_blank"
    rel="noopener noreferrer"
    class="hover:text-pink-500 transition duration-300"
  >
    <svg viewBox="0 0 24 24" class="w-5 h-5 fill-current">
      <path d="M7 2C4.2 2 2 4.2 2 7v10c0 2.8 2.2 5 5 5h10c2.8 0 5-2.2 5-5V7c0-2.8-2.2-5-5-5H7Zm0 2h10c1.7 0 3 1.3 3 3v10c0 1.7-1.3 3-3 3H7c-1.7 0-3-1.3-3-3V7c0-1.7 1.3-3 3-3Zm5 3.5A4.5 4.5 0 1 0 16.5 12 4.5 4.5 0 0 0 12 7.5Zm0 7A2.5 2.5 0 1 1 14.5 12 2.5 2.5 0 0 1 12 14.5ZM17.5 6.5a1 1 0 1 0 1 1 1 1 0 0 0-1-1Z"/>
    </svg>
  </a>

  <!-- X -->
  <a
    :href="member.x"
    target="_blank"
    rel="noopener noreferrer"
    class="hover:text-white transition duration-300"
  >
    <svg viewBox="0 0 24 24" class="w-5 h-5 fill-current">
      <path d="M18.244 2H21.5l-7.63 8.73L23 22h-7.4l-5.8-7.6L3.5 22H.244l8.17-9.35L0 2h7.6l5.25 6.9L18.244 2Z"/>
    </svg>
  </a>

  <!-- LinkedIn -->
  <a
    :href="member.linkind"
    target="_blank"
    rel="noopener noreferrer"
    class="hover:text-blue-500 transition duration-300"
  >
    <svg viewBox="0 0 24 24" class="w-5 h-5 fill-current">
      <path d="M4.98 3.5a2.49 2.49 0 1 0 0 4.98 2.49 2.49 0 0 0 0-4.98ZM3 9h4v12H3Zm7 0h3.6v1.7h.05a3.95 3.95 0 0 1 3.55-1.95c3.8 0 4.5 2.5 4.5 5.75V21h-4v-5.3c0-1.26 0-2.87-1.75-2.87s-2 1.37-2 2.78V21h-4Z"/>
    </svg>
  </a>

</div>


          </div>
        </div>

      </div>

    </div>
  </section>
</template>

<style scoped>
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
</style>
