<template>
  <div class="wrapper">
    <Header />
    <div class="layout">
      <Content />
      <Transition name="fade" appear>
        <Sidebar v-if="showSidebar" />
      </Transition>
    </div>
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import Header from './components/Header.vue';
import Sidebar from './components/Sidebar.vue';
import Content from './components/Content.vue';
import Footer from './components/Footer.vue';

const showSidebar = ref(window.innerWidth > 700);
const updateSidebar = () => (showSidebar.value = window.innerWidth > 700);

onMounted(() => window.addEventListener('resize', updateSidebar));
onUnmounted(() => window.removeEventListener('resize', updateSidebar));
</script>

<style>
body {
  background: #eee;
  margin: 0;
  font-family: Arial, sans-serif;
  overflow-y: auto;
}
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  overflow-x: auto;
}
.layout {
  display: flex;
  max-width: 800px;
  width: 100%;
  background: #fff;
  box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
  margin-top: 50px;
  min-width: 500px;
}

</style>
