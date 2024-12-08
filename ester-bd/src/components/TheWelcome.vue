<script setup lang="ts">
import { ref } from 'vue'

const open = ref<boolean>(false)
const selectedImageIndex = ref<number | null>(null);

const openPopup = () => {
  open.value = true
}

const selectImageIndex = (index: number) => {
  selectedImageIndex.value = index
}

const closePopup = (event: MouseEvent) => {
  if (!(event.target as HTMLElement).closest('.popup')) {
    open.value = false
  }
}
</script>

<template>
  <h1>Choose your blindbox</h1>
  <hr />
  <img src="@/assets/me blindbox.png" alt="" style="width: 15rem; cursor: pointer" @click="selectImageIndex(0)" :class="{ 'highlighted': selectedImageIndex === 0 }" />
  <img src="@/assets/me blindbox.png" alt="" style="width: 15rem; cursor: pointer" @click="selectImageIndex(1)" :class="{ 'highlighted': selectedImageIndex === 1 }" />
  <img src="@/assets/me blindbox.png" alt="" style="width: 15rem; cursor: pointer" @click="selectImageIndex(2)" :class="{ 'highlighted': selectedImageIndex === 2 }" />
  <button @click="openPopup()">Open</button>

  <!-- Popup for selected image -->
  <div v-if="open">
    <div class="overlay" @click="closePopup($event)"></div>
    <div class="popup">
      <img src="@/assets/me blindbox item.png" />
    </div>
  </div>
</template>

<style scoped>
img {
  width: 15rem;
}
img.highlighted {
  border: 2px solid rgb(193, 193, 255); /* You can customize the highlight as needed */
  background-color: rgb(88, 70, 90);
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 999;
}

.popup {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 2rem;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  z-index: 1000;
}
</style>
