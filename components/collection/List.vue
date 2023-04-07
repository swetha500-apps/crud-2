<template>
  <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">
          Transactions
        </h1>
        <p class="mt-2 text-sm text-gray-700">
          A table of placeholder stock market data that does not make any sense.
        </p>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        <button
          type="button"
          class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
          @click="openAddsidebar"
        >
          Projects
        </button>
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0"
                >
                  Name
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  ListName
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Details
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Specifications
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  ProjectAge
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  Logo
                </th>
                <th
                  scope="col"
                  class="whitespace-nowrap py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  DefaultImage
                </th>
                <th
                  scope="col"
                  class="relative whitespace-nowrap py-3.5 pl-3 pr-4 sm:pr-0"
                >
                  <span class="sr-only">Edit</span>
                </th>
                <th
                  scope="col"
                  class="relative whitespace-nowrap py-3.5 pl-3 pr-4 sm:pr-0"
                >
                  <span class="sr-only">Delete</span>
                </th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <tr v-for="project in props.projectData" :key="project.name">
                <td
                  class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0"
                >
                  {{ project.name }}
                </td>
                <td
                  class="whitespace-nowrap px-2 py-2 text-sm font-medium text-gray-900"
                >
                  {{ project.listing_type_name }}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-900">
                  {{ project.details }}
                </td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">
                  {{ project.specifications }}
                </td>
                <td class="whitespace-nowrap py-2 text-sm text-gray-500">
                  {{ project.age_of_the_project }}
                </td>
                <td class="whitespace-nowrap py-2 text-sm text-gray-500">
                  {{ project.logo_url }}
                </td>
                <td class="whitespace-nowrap py-2 text-sm text-gray-500">
                  {{ project.default_image_url }}
                </td>

                <div class="flex">
                  <PencilSquareIcon
                    @click="openEditsidebar(project)"
                    class="h-5 w-5 mr-3"
                    aria-hidden="true"
                  ></PencilSquareIcon>

                  <TrashIcon
                    @click="deleteProject(project.name)"
                    class="h-5 w-5"
                    aria-hidden="true"
                  ></TrashIcon>
                </div>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref, defineEmits, defineProps } from "vue";
import { PencilSquareIcon, TrashIcon } from "@heroicons/vue/24/outline";
const props = defineProps({
  projectData: {
    type: Object,
  },
});
const emit = defineEmits(["openAddSidebar", "openEditSidebar","deleteProject"]);
const openAddsidebar = () => {
  emit("openAddSidebar");
};
const openEditsidebar = (value) => {
  emit("openEditSidebar", value);
};
const deleteProject=(name)=>{
 emit("deleteNotes",name)

}
</script>
