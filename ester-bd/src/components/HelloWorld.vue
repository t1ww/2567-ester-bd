<script setup lang="ts">
defineProps<{
  msg: string
}>()
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      -- Dear Ester, I love you so much, it's been years since we've been together but I've always feel more and more loved from you.<br>
      <hr>
      -- I kept falling in love with you more and more everyday. You makes me happy and my life seems brighter everyday when I'm with you.<br>
      <hr>
      -- I'm so glad we're together, and I want you to know that I appreciate everything you've ever done for me.<br>
    </h3>
  </div>
</template>

<style scoped>
div {
  width: 30rem;
}

h1 {
  font-weight: 500;
  font-size: 2.6rem;
  position: relative;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}

hr {
  opacity: 15%;
}
</style>
