<script setup>
import IconCancel from './icons/IconCancel.vue'

defineProps({
  message: {
    type: Object,
    required: true,
  },
})

// console.log(prop.value)

defineEmits(['cancelMessage'])
</script>

<template>
  <div class="area__output">
    <button @click="$emit('cancelMessage')">
      <icon-cancel />
    </button>
    <div>{{ message.text }}</div>
  </div>
</template>

<style scoped>
.area__output {
  background: #e4f0ed;
  border-radius: 6px;
  min-height: 72px;
  padding-left: 6px;
  padding-right: 16px;
  padding-top: 16px;
  padding-bottom: 16px;
  display: flex;
  align-items: center;
  overflow: hidden;

  margin-bottom: 24px;
}

.area__output button {
  background: #e4f0ed;
  cursor: pointer;
  flex-shrink: 0;

  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
}

.area__output div {
  flex-grow: 1;
}
</style>
