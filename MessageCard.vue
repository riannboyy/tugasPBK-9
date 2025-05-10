<script setup>
import { ref } from 'vue';

const props = defineProps({
  message: {
    type: String,
    required: true
  }
});

const emit = defineEmits(['reply']);
const childReply = ref('');

const sendReply = () => {
  childReply.value = ' Hai Parent, Child di sini!';
  emit('reply', childReply.value);
};
</script>

<template>
  <div class="card">
    <slot name="header" />

    <div class="message-box">
       Pesan dari Parent: <strong>{{ message }}</strong>
    </div>

    <button class="btn-success" @click="sendReply">
       Kirim Balasan ke Parent
    </button>

    <div v-if="childReply" class="child-reply">
       <strong>Balasan Child:</strong> {{ childReply }}
    </div>

    <slot name="footer" />
  </div>
</template>

<style scoped>
.card {
  background: #fff;
  border: 1px solid #ccc;
  border-radius: 12px;
  padding: 24px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  margin-top: 20px;
}
.message-box {
  background: #f8f9fa;
  padding: 12px;
  border-radius: 6px;
  margin-bottom: 1rem;
}
.btn-success {
  background: #28a745;
  color: white;
  padding: 10px 20px;
  border-radius: 6px;
  font-weight: bold;
  border: none;
  cursor: pointer;
}
.child-reply {
  margin-top: 1rem;
  padding: 10px;
  background: #e3fcec;
  border: 1px solid #b7f5c9;
  border-radius: 6px;
  color: #155724;
}
.card-title {
  font-size: 1.3rem;
  margin-bottom: 0.8rem;
}
.footer {
  color: #999;
  margin-top: 1.2rem;
}
</style>