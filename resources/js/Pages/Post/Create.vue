<script setup>
import { reactive } from 'vue'
import { router } from '@inertiajs/vue3'
import {Link} from "@inertiajs/vue3";
import MainLayout from "@/Layouts/MainLayout.vue";

defineOptions({
  layout: MainLayout,
});

const form = reactive({
  title: '',
  content: '',
})

function store() {
  router.post(route('post.store'), form)
}

</script>

<template>
  <h1 class="text-lg mb-8">
    Добавить
  </h1>
  <Link :href="route('post.index')" class="text-sm border rounded-full p-1 px-4 text-center truncate inline-block ml-auto">
    Назад
  </Link>
  <form @submit.prevent="store">
    <div class="mb-4">
      <input v-model="form.title" placeholder="Название" class="w-full rounded-3xl border-gray-300 " type="text" name="" id="">
    </div>

    <div class="mb-4">
      <textarea v-model="form.content" class="w-full rounded-3xl border-gray-300 min-h-32" placeholder="Текст"></textarea>
    </div>

    <div>
      <button type="submit" class="bg-white rounded-full text-center text-black block p-2 border hover:bg-gray-50 w-full" >Опубликовать</button>
    </div>

  </form>
</template>

<style scoped>
</style>