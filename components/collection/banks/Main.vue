<template>
<CollectionBanksList @add="add"  :questions="questions"/>
<CollectionBanksAdd  v-if="isAdd" :key="addRender" @save="addQuestion"/>

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
const editPrefilledData=ref("")
// Get questions data using api call
const { data: questions } = await useLazyFetch(
  "https://v1-stark-db-orm.mars.hipso.cc/api/question-bank/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  {
    method: "GET",
    headers: authHeader,
  }
);
getData.value=questions.value
// Add questions data
const addQuestion = async (postBody: any) => {
  // Post call hits when click on save button
  const { data: response } = await useAuthLazyFetchPost("https://v1-stark-db-orm.mars.hipso.cc/api/question-bank/bulk", {
    method: "POST",
    headers: authHeader,
    body: [postBody],
  });
  getData.value.unshift(response.value);
};
</script>