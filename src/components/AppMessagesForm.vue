<script setup>
import { ref } from 'vue'

const newMessage = ref('')

const emit = defineEmits(['submit'])

const handleSubmit = () => {
  if (!newMessage.value) {
    return
  }
  emit('submit', newMessage.value)

  newMessage.value = ''
}
</script>
<template>
  <form @submit.prevent="handleSubmit">
    <div class="area__form">
      <div class="form_input">
        <label for="message1">Новое сообщение</label>
        <input v-model="newMessage" type="text" placeholder="Введите сообщение" id="message1" />
      </div>
      <button>Отправить</button>
    </div>
  </form>
</template>
<style scoped>
.area__form {
  display: flex;

  @media (max-width: 640px) {
    flex-wrap: wrap;
    justify-content: center;
  }
}

.form_input {
  flex-grow: 1;
  position: relative;
  height: 50px;

  @media (max-width: 640px) {
    width: 100%;
    margin-bottom: 24px;
  }
}

.form_input label {
  font-weight: 500;
  font-size: 12px;
  color: #8b939c;
  letter-spacing: 0.01em;
  padding-left: 3px;
  padding-right: 3px;

  position: absolute;
  background: #ffffff;

  top: -10px;
  left: 10px;
}

.form_input input {
  font: inherit;
  letter-spacing: 0.01em;

  height: 100%;
  width: 100%;

  padding: 0 12px;

  border-radius: 8px;
  border: 1px solid #dee2e8;
}

.form_input input::placeholder {
  font-family: 'Roboto', Arial, sans-serif;
  color: #2b312c;
  font-weight: normal;
  font-size: 14px;
  line-height: 23px;
}

.area__form button {
  flex-shrink: 0;
  margin-left: 16px;

  width: 183px;
  height: 50px;
  font: inherit;
  font-weight: 700;
  text-transform: uppercase;
  color: #ffffff;

  display: flex;
  align-items: center;
  justify-content: center;
  background-repeat: 8px;
  border-radius: 8px;
  background: linear-gradient(to left, #11a87b, #04694b);

  cursor: pointer;

  @media (max-width: 640px) {
    margin-left: 0;
  }
}
</style>
