<template>
  <div>
    <div class="heart-container">
      <img src="@/assets/1.jpg" alt="Decorated image" class="heart-image" />
    </div>
    <img
      v-for="(flower, index) in flowers"
      :key="index"
      :src="flower.src"
      :alt="flower.alt"
      class="flower"
      :style="{ top: flower.top, left: flower.left, right: flower.right }"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

interface Flower {
  src: string
  alt: string
  top?: string
  left?: string
  right?: string
  bottom?: string
}
const flowerSrc =
  'https://png.pngtree.com/png-vector/20231108/ourmid/pngtree-pink-flower-cute-png-image_10448174.png'
export default defineComponent({
  name: 'DecoratedImg',
  props: {
    flowers: {
      type: Array as () => Flower[],
      required: false,
      default: () => [
        { src: flowerSrc, alt: 'Flower 1', top: '25%', left: '-10px' },
        { src: flowerSrc, alt: 'Flower 2', top: '5%', right: '120px' },
        { src: flowerSrc, alt: 'Flower 3', top: '20%', right: '20px' },
        { src: flowerSrc, alt: 'Flower 4', top: '60%', left: '20px' },
        { src: flowerSrc, alt: 'Flower 5', top: '80%', right: '120px' },
        { src: flowerSrc, alt: 'Flower 6', top: '60%', right: '20px' },
      ],
    },
  },
})
</script>

<style scoped>
div {
  position: relative;
  width: 260px;
  height: 320px;
}
.heart-container {
  overflow: hidden;
}

.heart-image {
  width: 100%;
  height: 100%;
  mask:
    radial-gradient(at 70% 31%, #000 29%, #0000 30%),
    radial-gradient(at 30% 31%, #000 29%, #0000 30%),
    linear-gradient(#000 0 0) bottom/100% 50% no-repeat;
  clip-path: polygon(
    -41% 0,
    50% 91%,
    141% 0
  );
  object-fit: cover;
}

.flower {
  position: absolute;
  width: 40px;
  animation: float 4s infinite ease-in-out;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0) rotate(0);
  }
  50% {
    transform: translateY(-20px) rotate(15deg);
  }
}
</style>
