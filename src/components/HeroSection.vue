<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import gsap from 'gsap'

const heroRef = ref(null)
const mascotCardRef = ref(null)
let ctx = null

onMounted(() => {
  ctx = gsap.context(() => {
    // 1. Entrada em cascata (stagger: 0.2) dos elementos de texto do Hero
    gsap.from('.hero-animate', {
      y: 50,
      opacity: 0,
      duration: 0.8,
      stagger: 0.2,
      ease: 'power3.out',
    })

    // 2. Levitação contínua do card mascote LipeS.exe
    gsap.to(mascotCardRef.value, {
      y: -15,
      duration: 2.5,
      repeat: -1,
      yoyo: true,
      ease: 'sine.inOut',
    })
  }, heroRef.value)
})

onUnmounted(() => {
  ctx?.revert()
})
</script>

<template>
  <section
    id="inicio"
    ref="heroRef"
    class="relative overflow-hidden py-20 lg:py-28"
  >
    <!-- Brilho neon de fundo (ambient glow) -->
    <div
      class="pointer-events-none absolute -top-24 left-1/4 h-96 w-96 -translate-x-1/2 rounded-full bg-purple-600/15 blur-[120px]"
    ></div>
    <div
      class="pointer-events-none absolute right-10 bottom-0 h-80 w-80 rounded-full bg-fuchsia-600/10 blur-[110px]"
    ></div>

    <div
      class="mx-auto grid max-w-7xl grid-cols-1 items-center gap-12 px-6 lg:grid-cols-2 lg:gap-16"
    >
      <!-- Coluna da Esquerda: Textos -->
      <div class="flex flex-col items-start text-left">
        <!-- Subtítulo pequeno -->
        <span
          class="hero-animate mb-4 inline-flex items-center gap-2 rounded-full border border-purple-500/30 bg-purple-500/10 px-3.5 py-1.5 text-xs font-semibold tracking-wider text-purple-300 uppercase"
        >
          <span class="h-2 w-2 rounded-full bg-purple-400 shadow-[0_0_8px_#a855f7]"></span>
          Desenvolvedor Full Stack &amp; Criador Digital
        </span>

        <!-- Título Principal (h1) -->
        <h1
          class="hero-animate font-display text-4xl leading-tight font-bold tracking-tight text-gray-100 sm:text-5xl lg:text-6xl"
        >
          Hello world!
          <span
            class="block bg-gradient-to-r from-purple-400 via-purple-500 to-fuchsia-500 bg-clip-text text-transparent drop-shadow-[0_0_20px_rgba(147,51,234,0.35)]"
          >
            Sou o Felipe
          </span>
        </h1>

        <!-- Parágrafo de Apresentação -->
        <p
          class="hero-animate mt-6 max-w-xl text-base leading-relaxed text-gray-400 sm:text-lg"
        >
          Apaixonado por transformar ideias em interfaces modernas, rápidas e
          escaláveis. Minha jornada no desenvolvimento é guiada pela evolução
          constante — unindo a reatividade do <strong class="font-medium text-gray-200">Vue.js</strong>,
          a solidez do back-end em <strong class="font-medium text-gray-200">C#</strong> e a
          versatilidade do <strong class="font-medium text-gray-200">Python</strong> para construir
          soluções completas de ponta a ponta.
        </p>

        <!-- Botões de Ação -->
        <div class="hero-animate mt-8 flex flex-wrap items-center gap-4">
          <a
            href="#projetos"
            class="inline-flex items-center gap-2 rounded-lg bg-purple-600 px-6 py-3 text-sm font-semibold text-white shadow-[0_0_20px_rgba(147,51,234,0.4)] transition-all duration-300 hover:bg-purple-500 hover:shadow-[0_0_28px_rgba(168,85,247,0.65)]"
          >
            Ver projetos
            <svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13 7l5 5m0 0l-5 5m5-5H6" />
            </svg>
          </a>

          <a
            href="#contato"
            class="inline-flex items-center gap-2 rounded-lg border border-purple-500/70 bg-transparent px-6 py-3 text-sm font-semibold text-purple-300 transition-all duration-300 hover:border-purple-400 hover:bg-purple-600/15 hover:text-white"
          >
            Fale comigo
          </a>
        </div>

        <!-- Ícones de Redes Sociais -->
        <div class="hero-animate mt-8 flex items-center gap-4">
          <!-- GitHub -->
          <a
            href="https://github.com/"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="GitHub"
            class="group flex h-11 w-11 items-center justify-center rounded-lg border border-gray-800 bg-[#18181b] text-gray-400 transition-all duration-300 hover:border-purple-500/60 hover:text-purple-400 hover:shadow-[0_0_15px_rgba(147,51,234,0.3)]"
          >
            <svg class="h-5 w-5 fill-current" viewBox="0 0 24 24">
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.53 1.032 1.53 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
              />
            </svg>
          </a>

          <!-- LinkedIn -->
          <a
            href="https://linkedin.com/"
            target="_blank"
            rel="noopener noreferrer"
            aria-label="LinkedIn"
            class="group flex h-11 w-11 items-center justify-center rounded-lg border border-gray-800 bg-[#18181b] text-gray-400 transition-all duration-300 hover:border-purple-500/60 hover:text-purple-400 hover:shadow-[0_0_15px_rgba(147,51,234,0.3)]"
          >
            <svg class="h-5 w-5 fill-current" viewBox="0 0 24 24">
              <path
                d="M19 3a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V5a2 2 0 0 1 2-2h14m-.5 15.5v-5.3a3.26 3.26 0 0 0-3.26-3.26c-.85 0-1.84.52-2.28 1.3v-1.11h-2.79v8.37h2.79v-4.93c0-.77.62-1.4 1.39-1.4a1.4 1.4 0 0 1 1.4 1.4v4.93h2.75M6.88 8.56a1.68 1.68 0 0 0 1.68-1.68c0-.93-.75-1.69-1.68-1.69a1.69 1.69 0 0 0-1.69 1.69c0 .93.76 1.68 1.69 1.68m1.39 9.94v-8.37H5.5v8.37h2.77z"
              />
            </svg>
          </a>

          <!-- Email -->
          <a
            href="mailto:felipesrochaprofessor@gmail.com"
            aria-label="Email"
            class="group flex h-11 w-11 items-center justify-center rounded-lg border border-gray-800 bg-[#18181b] text-gray-400 transition-all duration-300 hover:border-purple-500/60 hover:text-purple-400 hover:shadow-[0_0_15px_rgba(147,51,234,0.3)]"
          >
            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8">
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
              />
            </svg>
          </a>
        </div>
      </div>

      <!-- Coluna da Direita: Avatar / Mascote LipeS.exe -->
      <div class="flex justify-center lg:justify-end">
        <div
          ref="mascotCardRef"
          class="relative flex aspect-square w-full max-w-sm flex-col items-center justify-center rounded-2xl border border-purple-500/30 bg-[#1a1a1f] p-8 shadow-[0_0_45px_rgba(147,51,234,0.18)]"
        >
          <!-- Detalhes Cyberpunk nos cantos -->
          <span class="absolute top-3 left-3 h-3 w-3 border-t-2 border-l-2 border-purple-500"></span>
          <span class="absolute top-3 right-3 h-3 w-3 border-t-2 border-r-2 border-purple-500"></span>
          <span class="absolute bottom-3 left-3 h-3 w-3 border-b-2 border-l-2 border-purple-500"></span>
          <span class="absolute bottom-3 right-3 h-3 w-3 border-b-2 border-r-2 border-purple-500"></span>

          <!-- Halo neon interno -->
          <div
            class="absolute h-48 w-48 rounded-full bg-purple-600/20 blur-2xl"
          ></div>

          <!-- Ilustração SVG do Urso Mascote Cyberpunk -->
          <div class="relative z-10 flex h-44 w-44 items-center justify-center">
            <svg
              viewBox="0 0 200 200"
              class="h-full w-full drop-shadow-[0_0_16px_rgba(168,85,247,0.55)]"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <!-- Orelhas do Urso -->
              <circle cx="52" cy="52" r="24" fill="#121214" stroke="#a855f7" stroke-width="4" />
              <circle cx="52" cy="52" r="11" fill="#9333ea" fill-opacity="0.35" />
              <circle cx="148" cy="52" r="24" fill="#121214" stroke="#a855f7" stroke-width="4" />
              <circle cx="148" cy="52" r="11" fill="#9333ea" fill-opacity="0.35" />

              <!-- Cabeça do Urso -->
              <rect
                x="38"
                y="48"
                width="124"
                height="112"
                rx="46"
                fill="#18181b"
                stroke="#a855f7"
                stroke-width="4"
              />

              <!-- Visor Cyberpunk -->
              <rect
                x="54"
                y="78"
                width="92"
                height="30"
                rx="12"
                fill="#09090b"
                stroke="#c084fc"
                stroke-width="2.5"
              />
              <!-- Olhos Neon no Visor -->
              <path d="M68 93L84 93" stroke="#d8b4fe" stroke-width="5" stroke-linecap="round" />
              <path d="M116 93L132 93" stroke="#d8b4fe" stroke-width="5" stroke-linecap="round" />

              <!-- Focinho -->
              <ellipse cx="100" cy="128" rx="22" ry="16" fill="#27272a" stroke="#9333ea" stroke-width="2" />
              <polygon points="100,118 92,126 108,126" fill="#c084fc" />
              <path d="M100 126V134M92 134Q100 139 108 134" stroke="#e9d5ff" stroke-width="2.5" stroke-linecap="round" />

              <!-- Cicatriz / Linha Cyber -->
              <path d="M136 62L126 74" stroke="#a855f7" stroke-width="2.5" stroke-linecap="round" />
            </svg>
          </div>

          <!-- Assinatura LipeS.exe -->
          <div class="relative z-10 mt-4 text-center">
            <span
              class="font-display text-2xl font-bold tracking-wider text-gray-100 drop-shadow-[0_0_10px_rgba(168,85,247,0.6)]"
            >
              LipeS<span class="text-purple-400">.exe</span>
            </span>
            <p class="mt-1 font-mono text-xs text-purple-400/80">
              STATUS: <span class="text-emerald-400">ONLINE</span> // SYS.READY
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
