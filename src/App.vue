<script setup>
import { ref } from 'vue'
// import { computed } from 'vue'

const trend = ref(0)
const tp = ref(0.0)
const sl = ref(0.0)

// computed()

</script>

<template>
  <div class="w-screen h-screen flex justify-center items-center">
    <div class="w-1/3 flex-col gap-3">
      <div class="w-full flex">
        <div class="w-1/3">
          <div class="text-xs text-center">Close</div>
          <input class="w-full" type="number"
            step=".01" min="0" placeholder="0.00" />
        </div>
        <div class="w-1/3">
          <div class="text-xs text-center">ATR</div>
          <input class="w-full" type="number"
            step=".01" min="0" placeholder="0.00" />
        </div>
        <div class="w-1/3">
          <div class="text-xs text-center">Ratio</div>
          <input class="w-full" type="number"
            step=".1" min="0" placeholder="0.0" />
        </div>
      </div>
      <div class="w-full flex gap-2">
        <div class="flex justify-center items-center gap-1">
          <input type="radio" value="0" v-model="trend" />
          <div>Bear</div>
        </div>
        <div class="flex justify-center items-center gap-1">
          <input type="radio" value="1" v-model="trend" />
          <div>Bull</div>
        </div>
        <div class="flex w-full">
          <div class="flex w-1/2">
            <div>TP</div>
            <div class="w-full text-center">{{ tp }}</div>
          </div>
          <div class="flex w-1/2">
            <div>SL</div>
            <div class="w-full text-center">{{ sl }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
