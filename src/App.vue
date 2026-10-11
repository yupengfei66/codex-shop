<script setup>
import { onBeforeUnmount, ref } from 'vue'
import HeroSection from './components/HeroSection.vue'
import MenuSection from './components/MenuSection.vue'
import ReservationDialog from './components/ReservationDialog.vue'
import SiteFooter from './components/SiteFooter.vue'
import SiteHeader from './components/SiteHeader.vue'
import StorySection from './components/StorySection.vue'
import VisitSection from './components/VisitSection.vue'

const reservationOpen = ref(false)
const reservationTrigger = ref(null)
const toastVisible = ref(false)
let toastTimer

function openReservation(trigger) {
  reservationTrigger.value = trigger
  reservationOpen.value = true
}

function showConfirmation() {
  toastVisible.value = true
  window.clearTimeout(toastTimer)
  toastTimer = window.setTimeout(() => {
    toastVisible.value = false
  }, 3600)
}

onBeforeUnmount(() => window.clearTimeout(toastTimer))
</script>

<template>
  <SiteHeader @reserve="openReservation" />

  <main>
    <HeroSection />
    <MenuSection />
    <StorySection />
    <VisitSection @reserve="openReservation" />
  </main>

  <SiteFooter />

  <ReservationDialog
    v-model="reservationOpen"
    :return-focus="reservationTrigger"
    @reserved="showConfirmation"
  />

  <Transition name="toast">
    <div v-if="toastVisible" class="toast-message" role="status" aria-live="polite">
      预约意向已填写好，正式上线后即可联系门店确认。
    </div>
  </Transition>
</template>
