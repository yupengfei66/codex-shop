<script setup>
import { menuItems } from '../data/menu.js'
</script>

<template>
  <section id="menu" class="menu-section section-shell" aria-labelledby="menu-title">
    <div class="section-kicker"><span>02</span><span>SEASONAL / DAILY</span></div>
    <div class="menu-heading">
      <div>
        <p class="eyebrow">今天的好味道</p>
        <h2 id="menu-title">熟悉的味道，<br /><em>认真地做。</em></h2>
      </div>
      <p class="menu-intro">跟着季节吃饭，<br />也给平常日子加一点好滋味。</p>
    </div>

    <div class="menu-grid">
      <article v-for="dish in menuItems" :key="dish.number" class="dish-card" :class="`dish-${dish.tone}`">
        <div class="dish-visual">
          <span class="dish-index">{{ dish.number }}</span>
          <span class="dish-label">{{ dish.label }}</span>
          <div class="dish-plate" aria-hidden="true">
            <span class="dish-food">{{ dish.icon }}</span>
            <span class="dish-orbit"></span>
          </div>
          <span class="dish-asterisk" aria-hidden="true">✳</span>
        </div>
        <div class="dish-info">
          <div class="dish-title-row">
            <h3>{{ dish.name }}</h3>
            <span>{{ dish.note }}</span>
          </div>
          <p>{{ dish.description }}</p>
        </div>
      </article>
    </div>
    <p class="menu-footnote"><span aria-hidden="true">✳</span> 菜单随时令调整，今天想吃什么，也欢迎和我们聊聊。</p>
  </section>
</template>
