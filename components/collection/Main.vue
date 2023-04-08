<template>
<CollectionList @add="add" :customFields="customFields"/>
<CollectionAdd  v-if="isAdd" :key="render" @save="saveCustomField"/>
</template>
<script lang="ts" setup>
import { ref,defineProps} from 'vue'
// Defining Props
const props = defineProps({
  url: {
    type: String,
    default: "https://v1-orm-lib.mars.hipso.cc/api/custom-fields/", 
         
  },
  isActive: {
    type: String,
    default: "1",
  },
  projectId: {
    type: String,
    default: "95",
  },
  // Email customFields for contacts, deal etc.
  entity: {
    type: String,
     default: "CONTACTS",
    
  },
});
// Authorization token
const authHeader = {
  Authorization:
    "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI",
};
const isAdd=ref(false)
const render=ref(0)
const getData=ref();
const add = () => {  
  isAdd.value = true;
  render.value++
};
// Get customFields data using api call
const { data: customFields } = await useLazyFetch(
  `${props.url}${props.entity}?offset=0&limit=100&sort_column=id&sort_direction=desc`,
  {
    method: "GET",
    headers: authHeader,
  }
);
getData.value=customFields.value
// Save customField data
const saveCustomField = async (postBody: any) => {
  // Post call hits when click on save button
  const { data: response } = await useLazyFetch(props.url, {
    method: "POST",
    headers: authHeader,
    body: postBody,
  });
  getData.value.unshift(response.value);
};
</script>