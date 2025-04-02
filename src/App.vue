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
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 500px;
  max-width: 800px;
  margin: 0 auto;
  overflow-x: auto;
  min-height: 100vh;
  padding-bottom: 50px;
  box-sizing: border-box;
}

.layout {
  display: flex;
  width: 100%;
  min-width: 500px;
  background: #fff;
}
</style>
