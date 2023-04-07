<template>
  <CollectionList
    @openAddSidebar="openAddSidebar"
    @openEditSidebar="openEditSidebar"
     @deleteProject="deleteProject"
    :projectData="projects"
    :key="render"
  />
  <div v-if="addSidebar" :key="Addrender">
    <CollectionAdd @postData="postData" />
  </div>
  <div v-if="editSidebar" :key="Editrender">
    <CollectionEdit
      :name="name"
      :listName="listName"
      :details="details"
      :specifications="specifications"
      :projectAge="projectAge"
      :logo="logo"
      :defaultImage="defaultImage"
    />
  </div>
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";
const render = ref(0);
const addSidebar = ref(false);
const editSidebar = ref(false);
const Addrender = ref(0);
const Editrender = ref(0);
const projects = ref("");
const name = ref("");
const listName = ref("");
const details = ref("");
const specifications = ref("");
const projectAge = ref("");
const logo = ref("");
const defaultImage = ref("");
const getData = useAuthLazyFetch(
  "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/?offset=0&limit=100&sort_column=id&sort_direction=desc",
  ""
);
projects.value = getData.data._rawValue;
const openAddSidebar = () => {
  Addrender.value++;
  addSidebar.value = true;
};
const individualData=ref("")
const openEditSidebar = (data: any) => {
  individualData.value=data
  name.value = data.name;
  listName.value = data.listing_type_name;
  details.value = data.details;
  specifications.value = data.specifications;
  projectAge.value = data.age_of_the_project;
  logo.value = data.logo_url;
  defaultImage.value = data.default_image_url;
  Editrender.value++;
  editSidebar.value = true;
};
 const postData=(value: any)=> {
  const postoptions = {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      Authorization: `Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
    },
    body: {
      name: value.name,
      listing_type_name: value.listName,
      category: "Residential",
      sub_category: "Apartment",
      status: "Fully Constructed",
      details: value.details,
      specifications: value.specifications,
      possession_date: "2023-04-06",
      age_of_the_project: value.projectAge,
      logo_url: value.logo,
      total_project_area: 0,
      metric: "sq.ft",
      default_image_url: value.defaultImage,
      visit_count: 0,
      rera_approved: true,
      approve_status: "Active",
    },
  };
  render.value++;
  const data = useAuthLazyFetchPost(
    "https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/",
    postoptions
  );
}
const  deleteProject=(id:any)=>{
    const deleteOptions = {
    method: "DELETE",
    headers: {
      "Content-Type": "application/json",
      Accept: "application/json",
      Authorization: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1IjoiN2ZiMzBkNzhmM2NmNGEwZmJiZWNkZjJkOGM2ZjNhMGEiLCJkIjoiMTY4MDA3NyIsInIiOiJzYSIsInAiOiJmcmVlIiwiYSI6ImZpbmRlci5pbyIsImwiOiJ1czEiLCJleHAiOjE2ODMyNzM0NzR9.QjMEQKeWqKdjLekJkiFGTdhJ3iwilHM5Aa9FEqbWvOI`,
    },
}
 const deleteData = useAuthLazyFetchDelete(
    `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${id}`,
    deleteOptions
  );
projects.value.forEach((item:any,index:any)=>{
    (item.uid==id)?
    projects.value.splice(index, 1):""
      }) 
}
const putData=(individualData:any)=> {
let body={
   name: individualData.value.name,
      listing_type_name: individualData.listName,
      category: "Residential",
      sub_category: "Apartment",
      status: "Fully Constructed",
      details: individualData.value.details,
      specifications: individualData.value.specifications,
      possession_date: "2023-04-06",
      age_of_the_project: individualData.value.projectAge,
      logo_url: individualData.value.logo,
      total_project_area: 0,
      metric: "sq.ft",
      default_image_url: individualData.value.defaultImage,
      visit_count: 0,
      rera_approved: true,
      approve_status: "Active",
}
const { data: items, pending } =    useAuthLazyFetchPut( `https://v1-orm-gharpe.mercury.infinity-api.net/api/projects/${individualData.value.uid}`,{body: JSON.stringify(body)})
projects.value.forEach((item:any,index:any)=>{
    if(item.uid==individualData.value.uid){
    item.name=individualData.value.name
    item.listName=individualData.value.listing_type_name
    item.details=individualData.value.details
    item.specifications=individualData.value.specifications
    individualData.value.age_of_the_project
    individualData.value.default_image_url
    individualData.value.logo_url
      }})
}
</script>
