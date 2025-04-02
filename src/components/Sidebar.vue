<template>
  <aside class="sidebar"></aside>
</template>
<style>
.sidebar {
  width: 300px;
  border-left: 1px solid #ccc;
  box-shadow: -15px 0 15px rgba(51, 51, 51, 0.5);
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}

.fade-enter-active {
  transition: opacity 250ms linear;
}

.fade-leave-active {
  transition: opacity 250ms ease-out;
}
</style>