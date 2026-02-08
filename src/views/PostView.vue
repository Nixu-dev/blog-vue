<script setup>
import { ref } from 'vue'
import { useRoute } from 'vue-router'

// Obtener ID desde la URL
const route = useRoute()
const postId = Number(route.params.id)

// Simulamos datos de ejemplo (puedes reemplazar esto luego por fetch)
const posts = [
  { id: 1, title: 'Mi primer post', content: 'Este post está hecho con Vue 3 🚀' },
  { id: 2, title: 'Aprendiendo v-for', content: 'Vue hace que renderizar listas sea muy simple' },
  { id: 3, title: 'Componentes reutilizables', content: 'Un mismo componente, muchos usos 😎' },
]

// Encontrar el post correspondiente
const post = ref(posts.find((p) => p.id === postId))
</script>

<template>
  <main v-if="post">
    <h1>{{ post.title }}</h1>
    <p>{{ post.content }}</p>
    <router-link to="/">← Volver al blog</router-link>
  </main>
  <main v-else>
    <h1>Post no encontrado</h1>
    <router-link to="/">← Volver al blog</router-link>
  </main>
</template>

<style scoped>
main {
  max-width: 600px;
  margin: 2rem auto;
  font-family: Arial, sans-serif;
  padding: 0 1rem;
}

h1 {
  margin-bottom: 1rem;
}

p {
  line-height: 1.5;
  color: #555;
  margin-bottom: 2rem;
}

a {
  color: #42b983;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}
</style>
