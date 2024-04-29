<template>
  <div id="app" class="container mt-5">
    <div class="input-group mb-3">
      <input v-model="message" type="text" class="form-control" placeholder="Enter a message">
      <div class="input-group-append">
        <button @click="sendMessage" class="btn btn-primary">Send</button>
      </div>
    </div>
    <div class="message-container">
      <div v-for="(msg, index) in messages" :key="index" class="message-item">
        <p :class="{ active: msg.isActive }" :style="{ color: msg.color, fontSize: msg.fontSize + 'px' }">{{ msg.text }}</p>
        <div class="btn-group btn-group-sm">
          <button @click="toggleActive(msg)" class="btn btn-secondary">Toggle Active</button>
          <button @click="changeColor(msg)" class="btn btn-secondary">Change Color</button>
          <button @click="changeFontSize(msg)" class="btn btn-secondary">Change Font Size</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: '',
      messages: []
    }
  },
  methods: {
    sendMessage() {
      this.messages.push({
        text: this.message,
        isActive: false,
        color: 'red',
        fontSize: 14
      });
      this.message = '';
    },
    toggleActive(msg) {
      msg.isActive = !msg.isActive;
    },
    changeColor(msg) {
      msg.color = msg.color === 'red' ? 'blue' : 'red';
    },
    changeFontSize(msg) {
      msg.fontSize += 2;
    }
  }
}
</script>

<style>
#app {
  background-image: url('../../latihan2/pp1.JPEG');
  background-size: cover;
  background-position: center;
  min-height: 100vh; /* Mengatur tinggi background untuk mengisi layar penuh */
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Styling lainnya sesuai kebutuhan */
.message-container {
  max-height: 300px;
  overflow-y: auto;
}

.message-item {
  margin-bottom: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}

.active {
  background-color: yellow;
}
</style>

