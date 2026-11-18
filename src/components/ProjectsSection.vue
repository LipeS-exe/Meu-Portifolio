<script setup>
import { onMounted, onUnmounted, ref } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const projectsSectionRef = ref(null)
let ctx = null

const projects = [
  {
    id: 1,
    title: 'Nexus Cyber Dashboard',
    description:
      'Painel analítico em tempo real para monitoramento de servidores, métricas de rede e alertas automatizados.',
    techs: ['Vue', 'Tailwind CSS', 'GSAP'],
    tag: 'FRONT-END',
    link: '#',
  },
  {
    id: 2,
    title: 'CoreFin API & Gestão',
    description:
      'Sistema robusto de controle financeiro empresarial com autenticação JWT, relatórios e arquitetura limpa.',
    techs: ['C#', '.NET', 'SQL Server'],
    tag: 'BACK-END',
    link: '#',
  },
  {
    id: 3,
    title: 'AutoBot Data Scraper',
    description:
      'Pipeline inteligente de automação e coleta de dados com processamento assíncrono e exportação estruturada.',
    techs: ['Python', 'FastAPI', 'Docker'],
    tag: 'AUTOMAÇÃO',
    link: '#',
  },
  {
    id: 4,
    title: 'DevHub Portfolio Engine',
    description:
      'Plataforma full stack integrando catálogo interativo de projetos, animações fluidas e integração com APIs.',
    techs: ['Vue', 'C#', 'Python'],
    tag: 'FULL STACK',
    link: '#',
  },
]

onMounted(() => {
  ctx = gsap.context(() => {
    gsap.from('.project-card', {
      scrollTrigger: {
        trigger: projectsSectionRef.value,
        start: 'top 80%',
        toggleActions: 'play none none none',
      },
      y: 50,
      opacity: 0,
      duration: 0.7,
      stagger: 0.15,
      ease: 'power3.out',
    })
  }, projectsSectionRef.value)
})

onUnmounted(() => {
  ctx?.revert()
})
</script>

<template>
  <section
    id="projetos"
    ref="projectsSectionRef"
    class="relative py-24"
  >
    <div class="mx-auto max-w-7xl px-6">
      <!-- Cabeçalho da Seção -->
      <div class="mb-14 text-center">
        <h2 class="font-display text-3xl font-bold tracking-tight text-gray-100 sm:text-4xl">
          <span class="text-purple-500 drop-shadow-[0_0_10px_rgba(168,85,247,0.6)]">[</span>
          Projetos
          <span class="text-purple-500 drop-shadow-[0_0_10px_rgba(168,85,247,0.6)]">]</span>
        </h2>
        <p class="mx-auto mt-3 max-w-2xl text-sm text-gray-400 sm:text-base">
          Alguns dos principais sistemas, interfaces e automações que desenvolvi
          aplicando boas práticas e tecnologias modernas.
        </p>
      </div>

      <!-- Grid de Projetos: 4 colunas no desktop -->
      <div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-4">
        <article
          v-for="project in projects"
          :key="project.id"
          class="project-card group flex flex-col overflow-hidden rounded-xl border border-gray-800/90 bg-[#18181b] transition-all duration-300 hover:-translate-y-1.5 hover:border-purple-500/60 hover:shadow-[0_0_30px_rgba(147,51,234,0.2)]"
        >
          <!-- Capa do Card (Visual Cyberpunk) -->
          <div
            class="relative flex h-44 w-full items-center justify-center overflow-hidden border-b border-gray-800 bg-gradient-to-br from-[#1f1630] via-[#15151a] to-[#121214]"
          >
            <!-- Grade decorativa sutil -->
            <div
              class="absolute inset-0 bg-[radial-gradient(#a855f7_1px,transparent_1px)] [background-size:16px_16px] opacity-15 transition-opacity duration-300 group-hover:opacity-30"
            ></div>

            <!-- Tag de categoria no canto -->
            <span
              class="absolute top-3 right-3 rounded border border-purple-500/40 bg-[#121214]/80 px-2.5 py-0.5 font-mono text-[10px] font-semibold tracking-wider text-purple-300 backdrop-blur-xs"
            >
              {{ project.tag }}
            </span>

            <!-- Ícone representativo -->
            <div
              class="relative z-10 flex h-14 w-14 items-center justify-center rounded-xl border border-purple-500/40 bg-purple-600/15 text-purple-400 shadow-[0_0_20px_rgba(147,51,234,0.3)] transition-transform duration-300 group-hover:scale-110"
            >
              <svg class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.8">
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4"
                />
              </svg>
            </div>
          </div>

          <!-- Corpo do Card -->
          <div class="flex flex-1 flex-col p-5">
            <h3
              class="font-display text-lg font-bold text-gray-100 transition-colors group-hover:text-purple-400"
            >
              {{ project.title }}
            </h3>

            <p class="mt-2 flex-1 text-sm leading-relaxed text-gray-400">
              {{ project.description }}
            </p>

            <!-- Badges de Tecnologias -->
            <div class="mt-4 flex flex-wrap gap-2">
              <span
                v-for="tech in project.techs"
                :key="tech"
                class="rounded-md border border-purple-500/25 bg-purple-500/10 px-2.5 py-1 text-xs font-medium text-purple-300"
              >
                {{ tech }}
              </span>
            </div>

            <!-- Link / Botão Ver Projeto -->
            <div class="mt-6 pt-2">
              <a
                :href="project.link"
                class="inline-flex w-full items-center justify-center gap-2 rounded-lg bg-purple-600/90 px-4 py-2.5 text-xs font-semibold tracking-wide text-white uppercase transition-all duration-200 hover:bg-purple-500 hover:shadow-[0_0_16px_rgba(168,85,247,0.5)]"
              >
                Ver projeto
                <svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M14 5l7 7m0 0l-7 7m7-7H3" />
                </svg>
              </a>
            </div>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>
