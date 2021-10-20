<script setup lang="ts">
import { defineProps} from 'vue'
import { computed } from 'vue-demi'

const props = defineProps<{ selectedValues: string[], onSelect: (value: string) => void }>()
const options = computed(()=>{
  var reasons = [
    {
      value: 'reason1',
      label: 'Reason1Label'
    },
    {
      value: 'reason2',
      label: 'Reason2Label'
    }]
  return reasons.map(r=>({
      value: r.value,
      label: r.label,
      disabled: props.selectedValues.some(s => s === r.value)
  }))
})

const handleChange = (values: string[]) => {
  props.onSelect(values[values.length - 1])
}
</script>

<template>
  <el-cascader :options="options" @change="handleChange"></el-cascader>
</template>