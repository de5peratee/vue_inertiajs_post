<script setup>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

defineOptions({
  layout: MainLayout,
});

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
      <Link :href="route('post.create')" class="bg-white rounded-full text-center text-black block p-2 border hover:bg-gray-100 hover:border- ">
        Add Post
      </Link>
    </div>

    <div v-if="posts" class="mt-8">
      <div v-for="post in posts" class="mb-4 p-4 border rounded-3xl">
<!--        <p class="text-gray-600 text-xs text-right">ID: {{ post.id }}</p>-->
        <h2 class="text-xl font-semibold">{{ post.title }}</h2>
        <p class="text-gray-600">{{ post.content }}</p>
        <p class="text-gray-600 text-xs mt-4 text-right" >{{ post.date }}</p>
<!--        <p class="text-gray-600">{{ post.updated_at }}</p>-->
        <div class="text-gray-600 text-xs mt-4 text-right">
          <Link :href="route('post.show', post.id)" class="bg-gray-100 p-1 px-4 rounded-full text-black">
            Show
          </Link>
        </div>

      </div>
    </div>

    <div v-else class="mt-8 text-gray-500">
      No posts available.
    </div>
  </div>
</template>

<style scoped>
</style>