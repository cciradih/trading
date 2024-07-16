<script setup>
import { ref } from 'vue'
import { computed } from 'vue'

const close = ref(0.0)
const atr = ref(0.0)
const ratio = ref(1.0)
const trend = ref(0)

const tp = computed(() => {
  if (trend.value == 0) {
    return close.value - atr.value * ratio.value
  }
  if (trend.value == 1) {
    return close.value + atr.value * ratio.value
  }
})

const sl = computed(() => {
  if (trend.value == 0) {
    return close.value + (atr.value * ratio.value) / 2
  }
  if (trend.value == 1) {
    return close.value - (atr.value * ratio.value) / 2
  }
})

const copy = (value) => {
  navigator.clipboard.writeText(value)
}

</script>

<template>
  <div class="w-screen h-screen flex justify-center items-center select-none">
    <div class="w-1/3 h-full flex-col">
      <div class="w-full py-2 flex gap-2">
        <div class="flex justify-center items-center gap-1">
          <input type="radio" value="0" v-model="trend" />
          <div>Bear</div>
        </div>
        <div class="flex justify-center items-center gap-1">
          <input type="radio" value="1" v-model="trend" />
          <div>Bull</div>
        </div>
      </div>
      <div class="w-full py-2 flex gap-2">
        <div class="w-1/3">
          <div class="text-xs text-center">Close</div>
          <input class="w-full" type="number" step=".01" min="0" v-model="close" />
        </div>
        <div class="w-1/3">
          <div class="text-xs text-center">ATR</div>
          <input class="w-full" type="number" step=".01" min="0" v-model="atr" />
        </div>
        <div class="w-1/3">
          <div class="text-xs text-center">Ratio</div>
          <input class="w-full" type="number" step=".1" min="0" v-model="ratio" />
        </div>
      </div>
      <div class="w-full py-2 flex gap-2">
        <div class="flex w-1/2">
          <div>TP</div>
          <div class="w-full text-center cursor-pointer" @click="copy(tp)">{{ tp.toFixed(2) }}</div>
        </div>
        <div class="flex w-1/2">
          <div>SL</div>
          <div class="w-full text-center cursor-pointer" @click="copy(sl)">{{ sl.toFixed(2) }}</div>
        </div>
      </div>
    </div>
  </div>
</template>
