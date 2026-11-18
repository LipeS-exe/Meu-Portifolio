<script setup>
import { ref } from 'vue'

const isMobileMenuOpen = ref(false)

const navLinks = [
  { label: 'Início', href: '#inicio' },
  { label: 'Projetos', href: '#projetos' },
  { label: 'Habilidades', href: '#habilidades' },
  { label: 'Contato', href: '#contato' },
]
</script>

<template>
  <header
    class="sticky top-0 z-50 w-full border-b border-purple-500/15 bg-[#121214]/85 backdrop-blur-md"
  >
    <div class="mx-auto flex max-w-7xl items-center justify-between px-6 py-4">
      <!-- Identidade / Logo -->
      <a
        href="#inicio"
        class="font-display text-base font-bold tracking-tight text-gray-100 transition-colors hover:text-purple-400 sm:text-lg"
      >
        Portfólio - Felipe Santos Rocha
        <span class="mx-1 text-purple-500">||</span>
        <span class="text-purple-400 drop-shadow-[0_0_8px_rgba(168,85,247,0.5)]">LipeS.exe</span>
      </a>

      <!-- Navegação Desktop -->
      <nav aria-label="Menu principal" class="hidden md:block">
        <ul class="flex items-center gap-8">
          <li v-for="link in navLinks" :key="link.href">
            <a
              :href="link.href"
              class="relative text-sm font-medium text-gray-300 transition-colors duration-200 hover:text-purple-400 after:absolute after:-bottom-1 after:left-0 after:h-0.5 after:w-0 after:bg-purple-500 after:transition-all after:duration-300 hover:after:w-full"
            >
              {{ link.label }}
            </a>
          </li>
        </ul>
      </nav>

      <!-- Botão Mobile -->
      <button
        type="button"
        class="inline-flex items-center justify-center rounded-lg border border-purple-500/30 p-2 text-gray-300 transition hover:bg-purple-600/10 hover:text-purple-400 md:hidden"
        aria-label="Abrir menu"
        @click="isMobileMenuOpen = !isMobileMenuOpen"
      >
        <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path
            v-if="!isMobileMenuOpen"
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M4 6h16M4 12h16M4 18h16"
          />
          <path
            v-else
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M6 18L18 6M6 6l12 12"
          />
        </svg>
      </button>
    </div>

    <!-- Menu Mobile -->
    <div
      v-if="isMobileMenuOpen"
      class="border-t border-purple-500/15 bg-[#121214] px-6 py-4 md:hidden"
    >
      <ul class="flex flex-col gap-3">
        <li v-for="link in navLinks" :key="link.href">
          <a
            :href="link.href"
            class="block rounded-md px-3 py-2 text-sm font-medium text-gray-200 transition hover:bg-purple-600/15 hover:text-purple-400"
            @click="isMobileMenuOpen = false"
          >
            {{ link.label }}
          </a>
        </li>
      </ul>
    </div>
  </header>
</template>
