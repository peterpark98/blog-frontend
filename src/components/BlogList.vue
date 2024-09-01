<template>
  <div>
    <h1>Blog List</h1>
    <ul>
      <li v-for="blog in blogs" :key="blog.id">
        {{ blog.title }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const blogs = ref([])

const fetchBlogs = async () => {
  try {
    const response = await axios.get('http://127.0.0.1:5000/api/blogs')
    blogs.value = response.data
  } catch (error) {
    console.error('Failed to fetch blogs:', error)
  }
}

onMounted(fetchBlogs)
</script>
