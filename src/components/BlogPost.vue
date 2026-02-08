<script setup>
const props = defineProps({
  title: String,
  content: String,
})
</script>

<template>
  <article class="post">
    <!-- Slot opcional: si no se pasa nada, se usa el title y content por defecto -->
    <slot>
      <h2>{{ props.title }}</h2>
      <p>{{ props.content }}</p>
    </slot>
  </article>
</template>

<style scoped>
.post {
  border: 1px solid #ddd;
  padding: 1rem;
  margin-bottom: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  background-color: #fff;
}

.post h2 {
  margin-top: 0;
  color: #333;
}

.post p {
  margin-bottom: 0;
  line-height: 1.4;
  color: #555;
}
</style>
