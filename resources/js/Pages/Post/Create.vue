<script setup>
import { reactive } from 'vue'
import { router } from '@inertiajs/vue3'
import {Link} from "@inertiajs/vue3";

const form = reactive({
  title: '',
  content: '',
})

function store() {
  router.post(route('post.store'), form)
}

</script>

<template>
  <div class="w-96 mx-auto pt-8">
    <h1 class="text-lg mb-8">
      Create
    </h1>
    <Link :href="route('post.index')" class="text-sm mb-8 text-sky-500">
      Back
    </Link>
    <form @submit.prevent="store">

      <div class="mb-4">
        <input v-model="form.title" placeholder="title" class="w-full rounded-3xl border-gray-300 " type="text" name="" id="">
      </div>

      <div class="mb-4">
        <textarea v-model="form.content" class="w-full rounded-3xl border-gray-300 min-h-32" placeholder="content"></textarea>
      </div>

      <div>
        <button type="submit" class="bg-sky-500 rounded-3xl text-center text-white block p-2 hover:bg-white hover:text-sky-500 border border-sky-500 w-full" >Store</button>
      </div>

    </form>
  </div>
</template>

<style scoped>
</style>