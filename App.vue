<script setup>
import { ref } from 'vue';
import MessageCard from './components/MessageCard.vue';

const parentMessage = ref(' Halo dari Parent!');
const responseMessage = ref('');

const updateMessage = () => {
  parentMessage.value = ' Pesan dari Parent sudah diperbarui!';
};

const handleChildReply = (msg) => {
  responseMessage.value = msg;
};
</script>

<template>
  <div class="app">
    <h1> Komunikasi Antar Komponen Vue 3</h1>
    <p class="subtitle">Gunakan Props, Emits, dan Slot secara elegan </p>

    <button class="btn-primary" @click="updateMessage">
       Perbarui Pesan ke Child
    </button>

    <MessageCard :message="parentMessage" @reply="handleChildReply">
      <template #header>
        <h2 class="card-title"> Komponen Child</h2>
      </template>

      <template #footer>
        <p class="footer"> Ini bagian footer dari parent (slot)</p>
      </template>
    </MessageCard>

    <div v-if="responseMessage" class="parent-reply">
       <strong>Child berkata:</strong> {{ responseMessage }}
    </div>
  </div>
</template>

<style scoped>
.app {
  max-width: 600px;
  margin: 2rem auto;
  text-align: center;
  font-family: 'Segoe UI', sans-serif;
}
.subtitle {
  margin-bottom: 1rem;
  color: #666;
}
.btn-primary {
  background: #007bff;
  color: white;
  padding: 10px 20px;
  border-radius: 8px;
  font-weight: bold;
  border: none;
  cursor: pointer;
  margin-bottom: 1.5rem;
}
.parent-reply {
  margin-top: 1.5rem;
  padding: 12px;
  background-color: #f0fdf4;
  border: 1px solid #a7f3d0;
  border-radius: 8px;
  color: #065f46;
  font-weight: 500;
}
</style>
