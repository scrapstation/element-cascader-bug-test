<script setup lang="ts">
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
const selectedValues = ref<string[]>([])
const handleSelect = (value:string)=>{
  if(selectedValues.value.some(x=>x === value)){
    return
  }
  selectedValues.value.push(value)
}
</script>

<template>
  已选择的原因：{{selectedValues}}
  <br>
  请选择原因1
  <br>
  <HelloWorld :selected-values="selectedValues" :onSelect="handleSelect"/>
  <br>
  请选择原因2
  <br>
  <HelloWorld :selected-values="selectedValues" :onSelect="handleSelect"/>
  <br>
</template>
