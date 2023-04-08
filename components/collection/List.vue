<template>
<div class="pr-4">
  <div class="lg:px-8 mt-8 px-4 py-3.5 sm:px-6">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">Custom Fields</h1>
        <p class="mt-2 text-sm text-gray-700">Organize your meetings better with more information.</p>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        <button type="button" class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"   @click="emit('add')">Add</button>
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-3">LABEL</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">TYPE</th>
                 <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">DESCRIPTION</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">PLACEHOLDER</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">MANDATORY</th>
                <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-3">
                  <span class="sr-only">Delete</span>
                </th>
              </tr>
            </thead>
            <tbody class="bg-white"> 
              <tr v-for="(field, fieldIdx) in customFields" :key="field.uid" :class="fieldIdx % 2 === 0 ? undefined : 'bg-gray-50'"  >
                <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-3">{{ field.name }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ field.type }}</td>
                 <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ field.type_data.description }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ field.type_data.placeholder }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500" v-if="field.type_data.is_required==1">Mandatory</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500" v-if="field.type_data.is_required==0">Not Mandatory</td>
                 <td class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-3"  @click="emit('edit',field)">
                  <a href="#" class="text-indigo-600 hover:text-indigo-900"
                    >Edit<span class="sr-only">, {{ field.name }}</span></a 
                  >
                </td>
                <td class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-3" @click="emit('delete',field.uid,fieldIdx)">
                  <a href="#" class="text-indigo-600 hover:text-indigo-900"
                    >Delete<span class="sr-only">, {{ field.name }}</span></a 
                  >
                </td>
               
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script setup lang="ts">
import {ref,defineEmits,defineProps} from "vue"
const props=defineProps({
  customFields:Object
})
// Define emits
const emit = defineEmits(["add","edit","delete"]);
</script>