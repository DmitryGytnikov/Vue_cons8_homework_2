<script setup>
import { computed, ref } from 'vue'

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

const newMessage = ref('')

const addMessage = () => {
  if (newMessage.value === '') return
  messages.value.push({
    id: messages.value.length + 1,
    text: newMessage.value,
    isHidden: false,
  })

  for (let i = 0; i < messages.value.length; i++) {
    messages.value[i].id = i
    console.log(i)
  }

  newMessage.value = ''
}

// setHiddenness
</script>

<template>
  <div>
    <div class="container">
      <p>Переменная newMessage {{ newMessage }}</p>
      <p>Переменная messages {{ messages }}</p>

      <div class="area">
        <div class="area__output">
          <button @click="setHiddenness">
            <svg width="14" height="15" viewBox="0 0 14 15" fill="none">
              <path
                d="M7.00061 6.08597L12.3039 0.782669L13.7181 2.19688L8.41483 7.50018L13.7181 12.8035L12.3039 14.2177L7.00061 8.9144L1.69731 14.2177L0.283098 12.8035L5.5864 7.50018L0.283098 2.19688L1.69731 0.782669L7.00061 6.08597Z"
                fill="#2C674D"
              />
            </svg>
          </button>
          <div>Сообщение 1</div>
        </div>
        <ul class="area__list">
          <li
            v-for="message in messages"
            :key="message.id"
            class="item"
            :class="{ 'item--hidden': message.isHidden }"
          >
            <div class="item__icon">
              <svg
                data-v-a98e0649=""
                width="16"
                height="16"
                viewBox="0 0 16 16"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M8.00053 6.39989L11.2005 3.19996L12.8004 4.79992L9.60049 7.99986L12.8004 11.1998L11.1998 12.8005L7.99984 9.60052L4.7999 12.8005L3.19993 11.2005L6.39987 8.00055L3.19993 4.80061L4.80059 3.19996L8.00053 6.39989Z"
                  fill="#2B312C"
                ></path>
              </svg>
            </div>
            <div class="item__text">{{ message.text }}</div>
          </li>
        </ul>

        <form @submit.prevent="addMessage">
          <div class="area__form">
            <div class="form_input">
              <label for="message1">Новое сообщение</label>
              <input
                v-model="newMessage"
                type="text"
                placeholder="Введите сообщение"
                id="message1"
              />
            </div>
            <button>Отправить</button>
          </div>
        </form>
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
