<script setup>
import MainLayout from "~/layouts/MainLayout.vue";
import {useUserStore} from "~/stores/user";

const userStore = useUserStore()

let posts = ref([])
let isPosts = ref(true)
let isLoading = ref(false)

onBeforeMount(() => {
  posts.value = [
    {
      name: 'John Weeks Dev',
      image: 'https://placehold.co/100',
      text: 'This is the title',
      picture: 'https://placehold.co/100',
    }
  ]
})
</script>

<template>
  <MainLayout>
    <div id="IndexPage" class="w-full overflow-auto">
      <div class="mx-auto max-w-[500px] overflow-hidden">
        <div id="Posts" class="px-4 max-w-[600px] mx-auto">
          <div class="text-white" v-if="isPosts" v-for="post in posts" :key="post">
            <Post :post="post" @isDeleted="posts = []"/>
          </div>
        </div>
      </div>
    </div>
  </MainLayout>
</template>

<style scoped>

</style>