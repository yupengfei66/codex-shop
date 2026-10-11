<script setup>
import { ref } from 'vue'

const emit = defineEmits(['reserve'])
const menuOpen = ref(false)
const menuToggle = ref(null)

function closeMenu() {
  menuOpen.value = false
}

function openReservation(event) {
  const returnFocus = menuOpen.value && window.matchMedia('(max-width: 680px)').matches
    ? menuToggle.value
    : event.currentTarget
  closeMenu()
  emit('reserve', returnFocus)
}
</script>

<template>
  <header class="site-header shell">
    <a class="brand" href="#top" aria-label="慢慢食堂首页" @click="closeMenu">
      <span class="brand-mark" aria-hidden="true">慢</span>
      <span class="brand-copy">
        <span class="brand-name">慢慢食堂</span>
        <span class="brand-note">好好吃饭 · 慢慢生活</span>
      </span>
    </a>

    <button
      ref="menuToggle"
      class="menu-toggle"
      type="button"
      :aria-expanded="menuOpen"
      aria-controls="primary-navigation"
      :aria-label="menuOpen ? '关闭导航' : '打开导航'"
      @click="menuOpen = !menuOpen"
    >
      <span aria-hidden="true">{{ menuOpen ? '×' : '☰' }}</span>
    </button>

    <nav
      id="primary-navigation"
      class="primary-nav"
      :class="{ 'is-open': menuOpen }"
      aria-label="主导航"
    >
      <a href="#menu" @click="closeMenu"><span class="nav-index">01</span>今日好味</a>
      <a href="#story" @click="closeMenu"><span class="nav-index">02</span>关于我们</a>
      <a href="#visit" @click="closeMenu"><span class="nav-index">03</span>来店坐坐</a>
      <button class="button button-small" type="button" @click="openReservation">
        留一张饭桌 <span aria-hidden="true">↗</span>
      </button>
    </nav>
  </header>
</template>
