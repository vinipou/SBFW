<template>
  <div>
    <transition name="fade" mode="out-in">
      <component :is="currentComponent" key="currentComponent" msg="Willkommen beim Studentischen Börsenforum Würzburg" />
    </transition>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';
import OnePage from './components/1.Page/1Page.vue';
import TwoPage from './components/2.Page/2Page.vue';

const components = [OnePage, TwoPage];
const currentComponentIndex = ref(0);

const currentComponent = ref(components[currentComponentIndex.value]);

// Einfache Funktion zum Wechseln der Komponente beim Scrollen
function onScroll() {
  // Wechselt die Komponente basierend auf der Scroll-Richtung
  currentComponentIndex.value = (currentComponentIndex.value + 1) % components.length;
  currentComponent.value = components[currentComponentIndex.value];
}

// Event-Listener für das Scroll-Event
window.addEventListener('scroll', onScroll);

// Bereinigen des Event-Listeners beim Unmount
onUnmounted(() => {
  window.removeEventListener('scroll', onScroll);
});

watch(currentComponentIndex, (newIndex) => {
  console.log(`Aktuelle Komponente ist: ${newIndex}`);
});
</script>

<style>
/* Globale Styles */
body, html {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0;
}
</style>
