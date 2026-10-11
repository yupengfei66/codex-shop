<script setup>
import { computed, nextTick, onBeforeUnmount, ref, watch } from 'vue'

const props = defineProps({
  modelValue: { type: Boolean, default: false },
  returnFocus: { type: Object, default: null },
})

const emit = defineEmits(['update:modelValue', 'reserved'])
const dialogRef = ref(null)
const formRef = ref(null)
const form = ref({ date: '', time: '', partySize: '', name: '' })
let previousOverflow = ''

function getLocalDate() {
  const now = new Date()
  const year = now.getFullYear()
  const month = String(now.getMonth() + 1).padStart(2, '0')
  const day = String(now.getDate()).padStart(2, '0')
  return `${year}-${month}-${day}`
}

const minimumDate = computed(getLocalDate)

function closeDialog() {
  emit('update:modelValue', false)
}

function getFocusableElements() {
  return [...dialogRef.value.querySelectorAll(
    'button:not([disabled]), input:not([disabled]), select:not([disabled]), [href], [tabindex]:not([tabindex="-1"])',
  )].filter((element) => element.getClientRects().length > 0)
}

function handleKeydown(event) {
  if (event.key === 'Escape') {
    event.preventDefault()
    closeDialog()
    return
  }

  if (event.key !== 'Tab' || !dialogRef.value) return

  const focusable = getFocusableElements()
  const first = focusable[0]
  const last = focusable[focusable.length - 1]
  if (!first || !last) return

  if (event.shiftKey && document.activeElement === first) {
    event.preventDefault()
    last.focus()
  } else if (!event.shiftKey && document.activeElement === last) {
    event.preventDefault()
    first.focus()
  }
}

function handleBackdropClick(event) {
  if (event.target === event.currentTarget) closeDialog()
}

function submitReservation() {
  if (!formRef.value?.reportValidity()) return
  emit('reserved')
  closeDialog()
  form.value = { date: '', time: '', partySize: '', name: '' }
}

watch(() => props.modelValue, async (isOpen) => {
  if (isOpen) {
    previousOverflow = document.body.style.overflow
    document.body.style.overflow = 'hidden'
    document.addEventListener('keydown', handleKeydown)
    await nextTick()
    dialogRef.value?.querySelector('input')?.focus()
  } else {
    document.body.style.overflow = previousOverflow
    document.removeEventListener('keydown', handleKeydown)
    await nextTick()
    props.returnFocus?.focus?.()
  }
}, { flush: 'post' })

onBeforeUnmount(() => {
  if (props.modelValue) document.body.style.overflow = previousOverflow
  document.removeEventListener('keydown', handleKeydown)
})
</script>

<template>
  <Teleport to="body">
    <div v-if="modelValue" class="modal-backdrop" @click="handleBackdropClick">
      <section
        ref="dialogRef"
        class="reservation-dialog"
        role="dialog"
        aria-modal="true"
        aria-labelledby="reservation-title"
        aria-describedby="reservation-description"
      >
        <button class="modal-close" type="button" aria-label="关闭预约窗口" @click="closeDialog">×</button>
        <p class="eyebrow"><span class="eyebrow-number">A SEAT FOR YOU</span></p>
        <h2 id="reservation-title">预约一张饭桌</h2>
        <p id="reservation-description" class="dialog-description">告诉我们大概的用餐时间和人数，准备好好招待你。</p>

        <form ref="formRef" @submit.prevent="submitReservation">
          <div class="form-row">
            <label class="field">
              到店日期
              <input v-model="form.date" class="form-control" required type="date" :min="minimumDate" />
            </label>
            <label class="field">
              到店时间
              <select v-model="form.time" class="form-control" required>
                <option disabled value="">请选择</option>
                <option>11:00—12:00</option>
                <option>12:00—14:00</option>
                <option>14:00—17:00</option>
                <option>17:00—19:00</option>
                <option>19:00—21:00</option>
              </select>
            </label>
          </div>
          <div class="form-row">
            <label class="field">
              用餐人数
              <select v-model="form.partySize" class="form-control" required>
                <option disabled value="">请选择</option>
                <option>1 位</option>
                <option>2 位</option>
                <option>3—4 位</option>
                <option>5—6 位</option>
                <option>7 位及以上</option>
              </select>
            </label>
            <label class="field">
              怎么称呼你
              <input v-model.trim="form.name" class="form-control" required type="text" placeholder="留下称呼就好" maxlength="20" />
            </label>
          </div>
          <button class="button dialog-submit" type="submit">提交预约意向 <span aria-hidden="true">→</span></button>
        </form>
        <p class="form-note">这是首页演示表单，正式营业前可接入门店电话或在线订座。</p>
      </section>
    </div>
  </Teleport>
</template>
