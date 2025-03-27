<script setup>
import { ref } from 'vue'

const props = defineProps({
  items: {
    type: Array,
    required: true,
    default: () => []
  }
})

const activeIndex = ref(null)

const toggleItem = (index) => {
  activeIndex.value = activeIndex.value === index ? null : index
}
</script>

<template>
  <div class="accordion">
    <div 
      v-for="(item, index) in items" 
      :key="index" 
      class="accordion-item"
    >
      <button 
        class="accordion-header" 
        @click="toggleItem(index)"
        :class="{ 'active': activeIndex === index }"
      >
        {{ item.title }}
        <Icon :name="activeIndex === index ? 'uil:minus-circle': 'uil:plus-circle'" class="accordion-icon"/>
      </button>
      <Transition name="accordion">
        <div 
          v-show="activeIndex === index"
          class="accordion-content"
        >
          <div class="accordion-content-inner">
            {{ item.content }}
          </div>
        </div>
      </Transition>
    </div>
  </div>
</template>

<style scoped>
.accordion {
  max-width: 850px;
  margin: 0 auto;
}

.accordion-item {
  border: 1px solid #e5e7eb;
  margin-bottom: 8px;
  border-radius: 10px;
}

.accordion-header {
  width: 100%;
  font-size: 15px;
  padding: 15px;
  background: transparent;
  border: none;
  text-align: left;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 500;
}

.accordion-header:hover {
  background: #f3f4f6;
}

.accordion-content {
  overflow: hidden;
}

.accordion-content-inner {
  text-align: left;
  padding: 16px;
  font-size: 13px;
}

.accordion-icon {
  min-width: 20px;
  min-height: 20px;
}

/* Стили для переходов */
.accordion-enter-active,
.accordion-leave-active {
  transition: all 0.3s ease;
  max-height: 1000px; /* Установите максимальную высоту в зависимости от контента */
}

.accordion-enter-from,
.accordion-leave-to {
  opacity: 0;
  max-height: 0;
}

.accordion-enter-to,
.accordion-leave-from {
  opacity: 1;
}
@media only screen and (min-width: 1024px){
  .accordion-header {
    width: 100%;
    font-size: 20px;
    padding: 16px;
  }

  .accordion-content {
    overflow: hidden;
  }

  .accordion-content-inner {
    font-size: 16px;
  }
}

</style>