<script setup>
import { ref, onMounted, nextTick } from "vue"
import { createClient } from "@supabase/supabase-js"

const config = useRuntimeConfig()

const supabase = createClient(
  config.public.supabaseUrl,
  config.public.supabaseAnonKey
)

const newMessage = ref("")
const messages = ref([])
const messageContainer = ref(null)
const loading = ref(true)

// FETCH DATA
const fetchMessages = async () => {
  const { data, error } = await supabase
    .from("komentar")
    .select("*")
    .order("created_at", { ascending: true })

  if (error) {
    console.error("Error fetch komentar:", error)
  } else {
    messages.value = data
  }

  loading.value = false

  await nextTick()
  scrollToBottom()
}

// SCROLL
const scrollToBottom = () => {
  if (messageContainer.value) {
    messageContainer.value.scrollTop =
      messageContainer.value.scrollHeight
  }
}

// SEND MESSAGE
const sendMessage = async () => {
  if (!newMessage.value.trim()) return

  const { error } = await supabase
    .from("komentar")
    .insert([
      { message: newMessage.value }
    ])

  if (error) {
    console.error("Error insert komentar:", error)
    return
  }

  newMessage.value = ""
  await fetchMessages()
}

onMounted(fetchMessages)
</script>

<template>
  <section class="relative flex items-center justify-center 
                  bg-[#0b0f18] px-6 py-28 overflow-hidden">

    <!-- RED GLOW BACKGROUND -->
    <div class="absolute -top-32 left-1/2 -translate-x-1/2 
                w-[500px] h-[500px] 
                bg-red-600/10 blur-[150px] 
                rounded-full pointer-events-none">
    </div>

    <div class="relative w-full max-w-2xl 
                bg-white/5 backdrop-blur-2xl 
                border border-white/10 
                rounded-3xl p-10 
                shadow-[0_20px_60px_rgba(0,0,0,0.6)]">

      <!-- TITLE -->
      <h1 class="text-center text-2xl font-semibold mb-10 
                 text-white tracking-wide">
        Text Anonim
      </h1>

      <!-- LOADING -->
      <div v-if="loading" class="text-center text-gray-400">
        Loading...
      </div>

      <!-- MESSAGE LIST -->
      <div
        v-else
        ref="messageContainer"
        class="bg-white/5 rounded-2xl p-5 
               h-[260px] overflow-y-auto space-y-4 mb-6
               border border-white/5"
      >
        <div
          v-for="msg in messages"
          :key="msg.id"
          class="flex items-start gap-3 group"
        >
          <div class="w-7 h-7 bg-white/10 rounded-full flex-shrink-0"></div>

          <p class="text-gray-300 text-sm leading-relaxed 
                    group-hover:text-white transition duration-300">
            {{ msg.message }}
          </p>
        </div>
      </div>

      <!-- INPUT -->
      <div class="flex items-center bg-white/5 
                  border border-white/5 
                  rounded-full px-6 py-3 
                  focus-within:border-red-500/40 
                  focus-within:bg-white/10
                  transition duration-300">

        <input
          v-model="newMessage"
          @keyup.enter="sendMessage"
          type="text"
          placeholder="Ketik pesan..."
          class="flex-1 bg-transparent outline-none 
                 text-sm text-white placeholder-gray-500"
        />

        <button
          @click="sendMessage"
          class="ml-4 text-red-500 hover:text-red-400 transition"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            class="w-6 h-6 fill-current"
          >
            <path d="M19.21 2.07 3.7 5.94c-2.06.52-2.32 3.34-.38 4.22l4.78 2.17c.98.45 2.04.61 3.07.5-.11 1.03.05 2.09.5 3.07l2.17 4.78c.88 1.94 3.7 1.68 4.22-.38l3.88-15.51c.41-1.64-1.08-3.13-2.72-2.72Z"/>
          </svg>
        </button>

      </div>

    </div>
  </section>
</template>
