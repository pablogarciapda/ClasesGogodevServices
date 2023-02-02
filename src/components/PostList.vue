<template>
  <h2>Listado de Post</h2>
  <ul>
    <li v-for="(post, index) in posts" :key="index">{{ post.title }}</li>
  </ul>
  {{ posts }}
</template>

<!-- Metodo COMPOSITION API con setup -->

<!-- <script lang="ts" setup>
  import PostService from '@/services/PostService'
  import { onMounted } from 'vue'

  const service = new PostService()
  const posts = service.getPosts()

  onMounted(async () => {
    await service.fetchAll()
  })
</script> -->

<!-- Metodo OPTION API -->

<script lang="ts">
  import PostService from '@/services/PostService'
  import { defineComponent } from 'vue'

  export default defineComponent({
    name: 'PostList',
    data() {
      const service = new PostService()
      const posts = service.getPosts()
      return { posts, service }
    },
    async mounted() {
      await this.service.fetchAll()
      console.log('El componente ' + this.$options.name + ' ha sido montado.')
    },
  })
</script>

<!-- Metodo COMPOSITION API -->

<!-- <script lang="ts">
  import PostService from '@/services/PostService'
  import { defineComponent, onMounted } from 'vue'

  export default defineComponent({
    name: 'PostList',
    setup() {
      const service = new PostService()
      const posts = service.getPosts()

      onMounted(async () => {
        await service.fetchAll()
      })

      return { posts }
    },
  })
</script> -->

<style scoped></style>
