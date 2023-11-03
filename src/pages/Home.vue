<template>
    <div class="chat-container mt-3">
      <div class="chat-messages">
        <div v-for="(message, index) in messages" :key="index" class="message" :class="{ 'user-message': message.isUser, 'other-message': !message.isUser }">
          <strong>{{ message.isUser ? 'Anda' : 'Teman' }}:</strong> {{ message.text }}
        </div>
      </div>
      <div class="input-group">
        <input type="text" class="form-control" v-model="newMessage" @keyup.enter="sendMessage">
        <button class="btn btn-dark" @click="sendMessage">Kirim</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newMessage: '',
        messages: []
      };
    },
    methods: {
      sendMessage() {
        if (this.newMessage.trim() !== '') {
          this.messages.push({ text: this.newMessage, isUser: true });
          this.newMessage = '';
        }
        // Simulasikan pesan balasan dari teman
        setTimeout(() => {
          this.messages.push({ text: 'Ini adalah pesan balasan dari teman.', isUser: false });
        }, 1000);
      }
    }
  };
  </script>
  
  <style scoped>
  .chat-container {
    max-width: 400px;
    margin: 0 auto;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 15px;
  }
  
  .chat-messages {
    height: 300px;
    overflow-y: hidden;
    overflow-x: hidden;
  }
  
  .message {
    margin: 10px 0;
  }
  
  .user-message {
    background-color: #e0e0e0;
    padding: 10px;
    border-radius: 5px;
  }
  
  .other-message {
    background-color: #1b1c1d;
    color: #fff;
    padding: 10px;
    border-radius: 5px;
  }
  
  .input-group {
    margin-top: 10px;
  }
  </style>
  