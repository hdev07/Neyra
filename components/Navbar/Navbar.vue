<template>
  <div>
    <!-- Navbar goes here -->
    <nav class="fixed w-full p-6 bg-transparent">
      <div class="flex items-center justify-between">
        <!-- Header logo -->
        <div>
          <Logo />
        </div>

        <!-- Mobile toggle -->
        <div class="md:hidden">
          <button @click="drawer">
            <svg
              class="h-8 w-8 fill-current text-black"
              fill="none"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path d="M4 6h16M4 12h16M4 18h16" />
            </svg>
          </button>
        </div>

        <!-- Navbar -->
        <div class="hidden md:block">
          <ul class="flex space-x-8 text-sm font-sans">
            <li>
              <a href="#Home" class="active border-b-2 border-blue-500 pb-1">Inicio</a>
            </li>
            <li>
              <a href="#Services" class="">Servicios</a>
            </li>
            <li>
              <a href="#Products" class="">Productos</a>
            </li>
            <li>
              <a href="#FAQ" class="">FAQ</a>
            </li>
            <li>
              <a href="#Contact-us" class="">Contactanos</a>
            </li>
            <li>
              <a
                href="#"
                class="cta bg-blue-500 hover:bg-blue-600 px-3 py-2 rounded text-white font-semibold"
              >Cotizaciones</a>
            </li>
          </ul>
        </div>

        <!-- Dark Background Transition -->
        <transition
          enter-class="opacity-0"
          enter-active-class="ease-out transition-medium"
          enter-to-class="opacity-100"
          leave-class="opacity-100"
          leave-active-class="ease-out transition-medium"
          leave-to-class="opacity-0"
        >
          <div
            v-show="isOpen"
            class="z-10 fixed inset-0 transition-opacity"
            @keydown.esc="isOpen = false"
          >
            <div class="absolute inset-0 bg-black opacity-50" tabindex="0" @click="isOpen = false"></div>
          </div>
        </transition>

        <!-- Drawer Menu -->
        <aside
          class="p-5 transform top-0 left-0 w-64 bg-white fixed h-full overflow-auto ease-in-out transition-all duration-300 z-30"
          :class="isOpen ? 'translate-x-0' : '-translate-x-full'"
        >
          <div class="close">
            <button class="absolute top-0 right-0 mt-4 mr-4" @click="isOpen = false">
              <svg
                class="w-6 h-6"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>
          </div>

          <span class="flex w-full items-center py-4 border-b" @click="isOpen = false">
            <Logo />
          </span>

          <ul class="divide-y font-sans">
            <li>
              <a href="#Home" class="my-4 inline-block" @click="isOpen = false">Inicio</a>
            </li>
            <li>
              <a href="#Services" class="my-4 inline-block" @click="isOpen = false">Servicios</a>
            </li>
            <li>
              <a href="#Products" class="my-4 inline-block" @click="isOpen = false">Productos</a>
            </li>
            <li>
              <a href="#FAQ" class="my-4 inline-block" @click="isOpen = false">FAQ</a>
            </li>
            <li>
              <a href="#Contact-us" class="my-4 inline-block" @click="isOpen = false">Contactanos</a>
            </li>
            <li>
              <a
                href="#"
                class="my-8 w-full text-center font-semibold cta inline-block bg-blue-500 hover:bg-blue-600 px-3 py-2 rounded text-white"
                @click="isOpen = false"
              >Cotizaciones</a>
            </li>
          </ul>
        </aside>
      </div>
    </nav>
  </div>
</template>

<script>
import Logo from "./Logo.vue";
export default {
  name: "NavbarComponent",
  components: { Logo },
  data() {
    return {
      isOpen: false
    };
  },
  watch: {
    isOpen: {
      immediate: true,
      handler(isOpen) {
        if (process.client) {
          if (isOpen)
            document.body.style.setProperty("overflow", "hidden");
          else
            document.body.style.removeProperty("overflow");
        }
      }
    }
  },
  mounted() {
    document.addEventListener("keydown", e => {
      if (e.keyCode === 27 && this.isOpen)
        this.isOpen = false;
    });
  },
  methods: {
    drawer() {
      this.isOpen = !this.isOpen;
    }
  }
}
</script>

<style>
</style>