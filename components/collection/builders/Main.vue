<template>
<CollectionBuildersList @add="add" @edit="edit" @delete="deleteconform" :employee="employeeDetails" @serachResults="searchResults"/>
<CollectionBuildersAdd  v-if="isAdd" :key="addRender" @save="addEmployee" />
<CollectionBuildersEdit v-if="isEdit" :key="editRender" :editPrefilledData="editPrefilledData" @saved="saved"/>
<CollectionBuildersDelete v-if="isDelete" :key="deleteRender" @deleteconform="deleteEmployee"/>
</template>
<script lang="ts" setup>
import { ref,defineProps} from 'vue'
const isAdd=ref(false)
const isEdit=ref(false)
const addRender=ref(0)
const isDelete=ref(false)
const editRender=ref(0)
const deleteRender=ref(0)
const getData=ref();
const editPrefilledData=ref("")
const editIndex=ref(0)
//open add sidebar
const add = () => {  
  isAdd.value = true;
  addRender.value++
};

//open edit sidebar
const edit = (editData:any,index:number) => {  
 editPrefilledData.value=editData
     editRender.value++   
     editIndex.value=index
     console.log("this.edit",editData,index)
  isEdit.value = true;

}
const deleteconform=()=>{
  isDelete.value=true
  deleteRender.value++
}
//getItems from localStorage
onMounted(() => {
  const employeeStoredData = localStorage.getItem("employeeData");
  if (employeeStoredData) {
    employeeDetails.value = JSON.parse(employeeStoredData);
  }
});
const employeeDetails=ref([])
//setItems in localStorage when new record is added
const addEmployee=(details:any)=>{
  employeeDetails.value.push(details);
  localStorage.setItem("employeeData", JSON.stringify(employeeDetails.value));
}
const saved=(editDetails:any)=>{
  employeeDetails.value[editIndex.value]=editDetails
   localStorage.setItem("employeeData", JSON.stringify(employeeDetails.value));
  
}
const deleteEmployee = (index: number) => {
  employeeDetails.value.splice(index, 1);
  localStorage.setItem("employeeData", JSON.stringify(employeeDetails.value));
   isDelete.value=false
};
const searchResults=(results:any)=>{

  console.log("results-->",results);
  
  employeeDetails.value=results
}
</script>