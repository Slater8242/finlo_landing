<script setup>
const props = defineProps({
  label: {
    type: String,
    required: true
  },
  type: {
    type: String,
    default: 'button'
  },
  disabled: {
    type: Boolean,
    default: false
  },
  styling: {
    type: String,
    default: 'style-1'
  }
})

const emit = defineEmits(['click'])
</script>

<template>
  <button :type="props.type" :disabled="props.disabled" @click="emit('click')" class="btn" :class="styling">
    {{ props.label }}
  </button>
</template>

<style scoped>
.style-1{
  background-color: #C6F806;
  border: none;
  color: #000;
}
.style-2{
  color: #615EFC;
  background-color: transparent;
  border: 1.5px solid rgba(97, 94, 252, 0.2);
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 10px;
  cursor: pointer;
  transition: 0.3s ease;
  width: 113px;
}

.style-1:hover {
  background-color: #82a103;
  color: #fff;
}

.btn:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}
</style>
