<template>
<CollectionList @add="add" @edit="edit" @delete="deletefield" :customFields="customFields"/>
<CollectionAdd  v-if="isAdd" :key="addRender" @save="addCustomField"/>
<CollectionEdit v-if="isEdit" :key="editRender" :editPrefilledData="editPrefilledData" @saved="saved"/>
</template>
<script lang="ts" setup>
import { ref,defineProps} from 'vue'
// Defining Props
const props = defineProps({
  url: {
    type: String,
    default: "https://v1-orm-lib.mars.hipso.cc/api/custom-fields/",   
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
const isEdit=ref(false)
const addRender=ref(0)
const editRender=ref(0)
const getData=ref();
//open add sidebar
const add = () => {  
  isAdd.value = true;
  addRender.value++
};
const editPrefilledData=ref("")
//open edit sidebar
const edit = (editData:any) => {  
  isEdit.value = true;
  editPrefilledData.value=editData
     editRender.value++
}
// Get customFields data using api call
const { data: customFields } = await useLazyFetch(
  `${props.url}${props.entity}?offset=0&limit=100&sort_column=id&sort_direction=desc`,
  {
    method: "GET",
    headers: authHeader,
  }
);
getData.value=customFields.value
// Add customField data
const addCustomField = async (postBody: any) => {
  // Post call hits when click on save button
  const { data: response } = await useLazyFetch(props.url, {
    method: "POST",
    headers: authHeader,
    body: postBody,
  });
  getData.value.unshift(response.value);
};
//Edit custom field
const saved=async(PutBody:any)=>{
    // Put call hits when click on save button
  const { data: response } = await useLazyFetch(`${props.url}${PutBody.uid}`, {
    method: "PUT",
    headers: authHeader,
    body: PutBody,
  });
};

// Delete customField based on uid
const deletefield = (uid: string,fieldIndex:any) => {
  const { data: response } = useLazyFetch(`${props.url}${uid}`, {
    method: "DELETE",
    headers: authHeader,
  });
   getData.value.splice(fieldIndex, 1);
};
</script>