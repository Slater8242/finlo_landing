<script setup>
import { defineProps, defineEmits, computed } from 'vue'

const props = defineProps({
  modelValue: Boolean, // Поддержка v-model
  label: String // Текст рядом с чекбоксом
})

const emit = defineEmits(['update:modelValue'])

const checked = computed({
  get: () => props.modelValue,
  set: (value) => emit('update:modelValue', value)
})
</script>

<template>
  <label class="custom-checkbox">
    <input type="checkbox" v-model="checked" class="hidden-checkbox" />
    <span class="checkbox-icon"></span>
    <span v-if="label" class="checkbox-label">{{ label }}</span>
  </label>
</template>

<style scoped>
.custom-checkbox {
  display: flex;
  align-items: center;
  cursor: pointer;
  user-select: none;
  text-align:left;
}

.hidden-checkbox {
  display: none;
}

.checkbox-icon {
  min-width: 20px;
  height: 20px;
  border: 2px solid #333;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s;
  margin-right: 8px;
  position: relative;
}

.checkbox-icon::after {
  content: '';
  width: 12px;
  height: 6px;
  border-left: 2px solid white;
  border-bottom: 2px solid white;
  transform: rotate(-45deg);
  opacity: 0;
  position: absolute;
  left: 1px;
  top: 2px;
}

.hidden-checkbox:checked + .checkbox-icon {
  background: #333;
}

.hidden-checkbox:checked + .checkbox-icon::after {
  opacity: 1;
}

.checkbox-label {
  font-size: 14px;
  color: #717882;
}


@media only screen and (max-width: 768px) {
  .checkbox-label{
    font-size: 12px;
    
  }
}
</style>
