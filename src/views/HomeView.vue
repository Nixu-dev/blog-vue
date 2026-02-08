<script setup>
import BlogPost from '@/components/BlogPost.vue'
import { ref } from 'vue'

const posts = ref([
  {
    id: 1,
    title: 'Mi primer post',
    content: 'Este post está hecho con Vue 3 🚀',
  },
  {
    id: 2,
    title: 'Aprendiendo v-for',
    content: 'Vue hace que renderizar listas sea muy simple',
  },
  {
    id: 3,
    title: 'Componentes reutilizables',
    content: 'Un mismo componente, muchos usos',
  },
])
// Fin array
// Variables para el formulario
const newTitle = ref('')
const newContent = ref('')

// Función para agregar un post
function addPost() {
  const id = posts.value.length + 1
  posts.value.push({
    id,
    title: newTitle.value,
    content: newContent.value,
  })
  // Limpiar el formulario
  newTitle.value = ''
  newContent.value = ''
}
// Fin codigo del formulario
</script>

<template>
  <main>
    <h1>My Blog</h1>

    <!-- Formulario para agregar un post -->
    <form @submit.prevent="addPost" class="post-form">
      <input v-model="newTitle" type="text" placeholder="Título del post" required />
      <textarea v-model="newContent" placeholder="Contenido del post" required></textarea>
      <button type="submit">Agregar Post</button>
    </form>

    <BlogPost v-for="post in posts" :key="post.id" :title="post.title" :content="post.content">
      <router-link :to="`/post/${post.id}`">
        <h2>{{ post.title }}</h2>
      </router-link>
      <p>{{ post.content }}</p>
    </BlogPost>
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
  text-align: center;
  margin-bottom: 2rem;
}

/* Formulario */
.post-form {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-bottom: 2rem;
}

.post-form input,
.post-form textarea {
  padding: 0.5rem;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 100%;
  box-sizing: border-box;
}

.post-form button {
  padding: 0.5rem;
  font-size: 1rem;
  background-color: #42b983;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s;
}

.post-form button:hover {
  background-color: #36976f;
}
</style>
