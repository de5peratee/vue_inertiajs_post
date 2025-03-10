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
      Posts
    </h1>
    <Link :href="route('post.index')" class="text-sm mb-2 text-sky-500">
      Back
    </Link>

    <div v-if="post" class="mt-8">
      <div class="mb-4 p-4 border rounded-3xl">
        <h2 class="text-xl font-semibold">{{ post.title }}</h2>
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