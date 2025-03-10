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
  <h1 class="text-lg mb-8">
    Посты
  </h1>
  <div>
    <Link :href="route('post.create')"
          class="bg-white rounded-full text-center text-black block p-2 border hover:bg-gray-50">
      Добавить пост
    </Link>
  </div>

  <div v-if="posts" class="mt-8">
    <div v-for="post in posts" class="flex flex-row mt-2 rounded-3xl">
        <div class="basis-11/12 p-4 border rounded-3xl box-border bg-white">
          <h2 class="text-xl font-semibold">{{ post.title }}</h2>
          <p class="text-gray-600 break-words max-w-64">{{ post.content }}</p>
          <div class="text-gray-600 text-xs mt-4 text-right flex flex-row flex-nowrap">
            <div class="border rounded-full p-1 px-4 text-center truncate inline-block ml-auto" title="{{ post.date }}">
              {{ post.date }}
            </div>

            <Link :href="route('post.show', post.id)"
                  class="hover:bg-gray-50 border rounded-full p-1 text-center flex items-center justify-center gap-1">
              <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"
                   class="w-4 h-4 stroke-current text-black stroke-2">
                <path fill="none" stroke-linecap="round" stroke-linejoin="round" d="M18 6L6 18M8 6h10v10"/>
              </svg>
            </Link>

          </div>
        </div>
        <div class="">

          <!--        delete-->
          <div class="h-16 bg-white hover:bg-red-200 cursor-pointer ml-2 p-4 border-x border-t rounded-t-3xl box-border flex items-center justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 stroke-current text-black stroke-1" viewBox="0 0 1024 1024">
              <path fill="#000000" d="M360 184h-8c4.4 0 8-3.6 8-8zh304v-8c0 4.4 3.6 8 8 8h-8v72h72v-80c0-35.3-28.7-64-64-64H352c-35.3 0-64 28.7-64 64v80h72zm504 72H160c-17.7 0-32 14.3-32 32v32c0 4.4 3.6 8 8 8h60.4l24.7 523c1.6 34.1 29.8 61 63.9 61h454c34.2 0 62.3-26.8 63.9-61l24.7-523H888c4.4 0 8-3.6 8-8v-32c0-17.7-14.3-32-32-32M731.3 840H292.7l-24.2-512h487z"/>
            </svg>
          </div>

          <!--        update-->
          <div class="h-16 bg-white hover:bg-gray-50 cursor-pointer ml-2 p-4 border rounded-b-3xl box-border flex items-center justify-center">
            <svg xmlns="http://www.w3.org/2000/svg" class="w-4 h-4 stroke-current text-black stroke-1"
                 viewBox="0 0 24 24">
              <g fill="none" stroke="#000000" stroke-linecap="round" stroke-linejoin="round" stroke-width="2">
                <path
                    d="m16.475 5.408l2.117 2.117m-.756-3.982L12.109 9.27a2.118 2.118 0 0 0-.58 1.082L11 13l2.648-.53c.41-.082.786-.283 1.082-.579l5.727-5.727a1.853 1.853 0 1 0-2.621-2.621"/>
                <path d="M19 15v3a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V7a2 2 0 0 1 2-2h3"/>
              </g>
            </svg>
          </div>
        </div>
    </div>
  </div>

  <div v-else class="mt-8 text-gray-500">
    НЕТ ПОСТИКОВ!
  </div>
</template>

<style scoped>
</style>