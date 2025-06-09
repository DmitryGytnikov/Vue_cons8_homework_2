<script setup>
import IconCancelStatus from './icons/IconCancelStatus.vue'
defineProps({
  messages: {
    type: Array,
    required: true,
  },
})
</script>
<template>
  <ul class="area__list">
    <li
      v-for="message in messages"
      :key="message.id"
      class="item"
      :class="{ 'item--hidden': message.isHidden }"
    >
      <div class="item__icon">
        <IconCancelStatus />
      </div>
      <div class="item__text">{{ message.text }}</div>
    </li>
  </ul>
</template>

<style scoped>
.area__list {
  padding: 16px;
  padding-bottom: 99px;
  margin-bottom: 24px;
}

.item {
  display: flex;
  align-items: center;
  justify-content: center;

  margin-bottom: 8px;
}

.item__icon {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 5px;

  width: 16px;
  height: 16px;
}

.item svg {
  display: none;
}

.item.item--hidden svg {
  display: block;
}

.item__text {
  flex-grow: 1;
  line-height: 24px;
}
</style>
