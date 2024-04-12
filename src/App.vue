<script setup lang="ts">
import { onErrorCaptured, ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})

const menuIsOpen = ref(false)

</script>

<template>
  <div class="bg-red-300 h-dvh w-52">
    <header>
      <nav>
        <ul>
          <li>
            <RouterLink to="/" class="text-red-500 underline"> Accueil </RouterLink>
          </li>
        </ul>
      </nav>
    </header>
    <RouterView v-slot="{ Component }">
      <Suspense>
        <component :is="Component" />
      </Suspense>
    </RouterView>
    
    <button @pointerdown="menuIsOpen = !menuIsOpen"
    aria-controls="mainNav"
    aria-expanded="true"
    class="rounded-full border-2 border-red-600 bg-red-300 px-2"
    >
    menu
    </button>
    <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
    <Transition
    class="transition-transform duration-500"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="-translate-x-full"
    >
    <nav v-show="menuIsOpen" id="mainNav">
    <ul>
      <li><a href="#">item 1</a></li>
      <li><a href="#">item 2</a></li>
      <li><a href="#">item 3</a></li>
    </ul>
    </nav>
    </Transition>
  </div>
</template>

