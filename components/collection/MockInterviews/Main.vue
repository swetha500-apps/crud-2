<template>
<CollectionMockInterviewsList @add="add"  :interviews="getData"/>
<CollectionMockInterviewsAdd  v-if="isAdd" :key="addRender" @save="addTest"/>

</template>
<script lang="ts" setup>
import { ref} from 'vue'
// Authorization token
const authHeader = {
  Authorization:
    "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI",
};
const isAdd=ref(false)
const addRender=ref(0)
const getData=ref();
//open add sidebar
const add = () => {  
  isAdd.value = true;
  addRender.value++
};
// Get interviews data using api call
const { data: interviews } = await useLazyFetch(
  "https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  {
    method: "GET",
    headers: authHeader,
  }
);
getData.value=interviews.value
// Add interviews data
const addTest = async (postBody: any) => {
  // Post call hits when click on save button
  const { data: response } = await useAuthLazyFetchPost("https://v7-stark-db-orm.mercury.infinity-api.net/api/mock-interviews/", {
    method: "POST",
    headers: authHeader,
    body: postBody,
  });
  getData.value.unshift(postBody);
};
</script>