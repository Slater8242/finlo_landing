<script setup>
const props = defineProps({
  show: {
    type: Boolean,
    required: true,
  },
});

const emit = defineEmits(["close"]);

function closePopup() {
  emit("close");
}

onMounted(() => {
  watchEffect(() => {
    if (props.show) {
      document.body.classList.add("no-scroll");
    } else {
      document.body.classList.remove("no-scroll");
    }
  });
});
</script>

<template>
  <div v-if="show" class="popup-overlay" @click.self="closePopup">
    <div class="popup-content">
      <button class="close-button" @click="closePopup">&#10005;</button>
      <slot></slot>
    </div>
  </div>
</template>


<style scoped>
.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.popup-content {
  position: relative;
  background: white;
  padding: 30px 52px 42px 40px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  width: 90%;
  height: 90%;
  overflow-y: auto;
}

.close-button {
  position: absolute;
  top: 20px;
  right: 32px;
  background: transparent;
  border: none;
  font-size: 20px;
  cursor: pointer;
  color: #000;
}
:global(.no-scroll) {
  overflow: hidden;
  height: 100vh;
}

@media only screen and (min-width: 1024px) {
.popup-content{
  width: auto;
  height: auto;
  max-height: 80vh;
}
}
</style>