<script setup>
const emit = defineEmits(['reserve'])

function openReservation(event) {
  emit('reserve', event.currentTarget)
}
</script>

<template>
  <section id="visit" class="visit-section section-shell" aria-labelledby="visit-title">
    <div class="visit-card">
      <div class="visit-marker" aria-hidden="true">04<br />COME IN</div>
      <div class="visit-copy">
        <p class="eyebrow">饭桌已经收拾好啦</p>
        <h2 id="visit-title">今天，来店里坐坐？</h2>
        <p>一个人吃饭、带家人来，或和朋友慢慢聊，我们都欢迎。</p>
        <div class="visit-details">
          <span><span aria-hidden="true">◷</span> 每日 11:00—21:30</span>
          <span><span aria-hidden="true">⌂</span> 温暖小店，欢迎带家人来</span>
        </div>
      </div>
      <button class="button button-light" type="button" @click="openReservation">
        预约一张饭桌 <span aria-hidden="true">↗</span>
      </button>
      <span class="visit-decoration" aria-hidden="true">慢慢<br />吃饭</span>
    </div>
  </section>
</template>
