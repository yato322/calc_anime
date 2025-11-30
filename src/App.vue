<script setup lang="ts">
import { UiButton, UiInput, UiSelect, UiCardResult } from 'calc_anime'
import { useIpCalculator } from './components/useIpCalculator'

const {
  ip,
  mask,
  options,
  isShowResult,
  isIpValid,
  networkAddress,
  addressesCount,
  showResult,
} = useIpCalculator()
</script>

<template>
  <form class="form">
 <UiInput v-model="ip" placeholder="Введите IP адрес" />

  <UiSelect :options="options" v-model="mask" />

  <UiButton variant="primary" :isDisabled="!isIpValid()" @click="showResult">Рассчитать</UiButton>
  </form>
<UiCardResult v-if="isShowResult && isIpValid()" :ip="ip" :mask="mask" :networkAddress="networkAddress" :addressesCount="addressesCount" />
</template>

<style>
.form {
  display: flex;
  gap: 4px;
}
</style>
