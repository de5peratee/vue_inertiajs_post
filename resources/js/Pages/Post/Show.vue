<script setup>
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

defineOptions({
  layout: MainLayout,
});

defineProps({
  post: {
    type: Array,
    required: true,
  },
});

</script>

<template>
    <h1 class="text-lg mb-8">
      Пост
    </h1>
    <Link :href="route('post.index')" class="text-sm border rounded-full p-1 px-4 text-center truncate inline-block ml-auto">
      Назад
    </Link>

    <div v-if="post" class="mt-8">
      <div class="mb-4 p-4 border rounded-3xl">
        <h2 class="text-xl">{{ post.title }}</h2>
        <p class="text-gray-600">{{ post.content }}</p>
        <p class="text-gray-600 text-xs mt-4 text-right" >{{ post.date }}</p>
      </div>
    </div>

    <div v-else class="mt-8 text-gray-500">
      No posts available.
    </div>
</template>

<style scoped>
</style>