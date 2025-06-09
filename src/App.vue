<script setup>
import { computed, ref } from 'vue'

import AppMessages from './components/AppMessages.vue'
import AppMessagesForm from './components/AppMessagesForm.vue'
import AppOutput from './components/AppOutput.vue'

const messages = ref([
  {
    id: 0,
    text: 'Сообщение 1',
    isHidden: false,
  },
  {
    id: 1,
    text: 'Сообщение 2',
    isHidden: false,
  },
  {
    id: 2,
    text: 'Сообщение 3',
    isHidden: true,
  },
])

const addMessage = (value) => {
  messages.value.push({
    id: messages.value.length + 1,
    text: value,
    isHidden: false,
  })

  for (let i = 0; i < messages.value.length; i++) {
    messages.value[i].id = i
    // console.log(i)
  }
}

const currentMessageIndex = ref(0)

const allowedMessages = computed(() => {
  return messages.value.filter((message) => !message.isHidden)
})

const currentMessage = computed(() => {
  const newCurrentIndex = (currentMessageIndex.value + 1) % allowedMessages.value.length

  return allowedMessages.value[newCurrentIndex] || { text: 'Ничего' }
})

const cancelMessage = (id) => {
  const message = messages.value.find((message) => message.id === id)

  if (!message) {
    return
  }
  message.isHidden = true
}

const messageTimer = 2000
setInterval(() => currentMessageIndex.value++, messageTimer)
</script>

<template>
  <div>
    <div class="container">
      <div class="area">
        <app-output
          :message="currentMessage"
          @cancel-message="cancelMessage(currentMessage.id)"
        ></app-output>
        <app-messages :messages="messages"></app-messages>
        <app-messages-form @submit="addMessage"></app-messages-form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 705px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.area {
  box-shadow: 0 1rem 3rem rgba(0, 0, 0, 0.175);
  padding: 32px;
}
</style>
