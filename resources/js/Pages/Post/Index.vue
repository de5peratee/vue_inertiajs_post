<script setup>
import {Link} from "@inertiajs/vue3";

defineProps({
  posts: {
    type: Array,
    required: true,
  },
});

</script>

<template>
  <div class="w-96 mx-auto pt-8">
    <h1 class="text-lg mb-8">
      Posts
    </h1>
    <div>
      <Link :href="route('post.create')" class="bg-sky-500 rounded-full text-center text-white block p-2 w-32 hover:bg-white hover:text-sky-500 border border-sky-500">
        Add Post
      </Link>
    </div>

    <div v-if="posts.length > 0" class="mt-8">
      <div v-for="post in posts" :key="post.id" class="mb-4 p-4 border rounded-lg">
        <h2 class="text-xl font-semibold">{{ post.title }}</h2>
        <p class="text-gray-600">{{ post.content }}</p>
      </div>
    </div>

    <div v-else class="mt-8 text-gray-500">
      No posts available.
    </div>
  </div>
</template>

<style scoped>
</style>