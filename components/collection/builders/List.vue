<template>
  <div class="pr-4">
    <div class="lg:px-8 mt-8 px-4 py-3.5 sm:px-6 flex flex-row">
      <div class="sm:flex sm:items-center">
        <div class="sm:flex-auto">
          <!--search employees-->
          <div class="mt-2">
            <input
            v-model="searchTerm"
              type="search"
              name="serach"
              id="search"
              class="block rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
              placeholder="search"
              @input="searchArray(searchTerm)"
            />
          </div>
        </div>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none ">
        <button
          type="button"
          class="float-right block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
          @click="emit('add')"
        >
          Add
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
                  class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-3"
                >
                  S No
                </th>
                <th
                  scope="col"
                  class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-3"
                >
                  NAME
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  AGE
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  GENDER
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  DATE OF JOINING
                </th>
                <th
                  scope="col"
                  class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900"
                >
                  DESIGNATION
                </th>
                <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-3">
                  <span class="sr-only">Delete</span>
                </th>
              </tr>
            </thead>
            <tbody class="bg-white">
              <tr
                v-for="(item, itemIdx) in employee"
                :key="item.uid"
                :class="itemIdx % 2 === 0 ? undefined : 'bg-gray-50'"
              >
              <td
                  class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-3"
                >
                  {{ itemIdx+1}}
                </td>
                <td
                  class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-3"
                >
                  {{ item.name }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ item.age }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500" >
                  {{item.gender}}
                </td>
                 
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
               
                  {{ new Date(item.doj).toLocaleDateString('en-US', { year: 'numeric', month: 'long', day: 'numeric' }) }}
                </td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">
                  {{ item.designation }}
                </td>

                <td
                  class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-3"
                  @click="emit('edit', item,itemIdx)"
                >
                  <a href="#" class="text-indigo-600 hover:text-indigo-900"
                    >Edit<span class="sr-only">, {{ item.name }}</span></a
                  >
                </td>
                <td
                  class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-3"
                  @click="emit('delete',itemIdx)"
                >
                  <a href="#" class="text-indigo-600 hover:text-indigo-900"
                    >Delete<span class="sr-only">, {{ item.name }}</span></a
                  >
                </td>
              </tr> 
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineEmits, defineProps } from "vue";
// Defining Props
const props = defineProps({
  employee: {
    type: Array,   
  }
});
const searchTerm=ref("")
// Define emits
const emit = defineEmits(["add", "edit", "delete","serachResults"]);
const searchArray = (searchTerm:any) => {
  let results =  props.employee.filter((item:any) => item.name.includes(searchTerm)) ;

emit('serachResults',results)
};
</script>
