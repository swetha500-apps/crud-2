<template>
<div class="pr-4">
  <div class="lg:px-8 mt-8 px-4 py-3.5 sm:px-6">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">BUILDERS</h1>
        <p class="mt-2 text-sm text-gray-700">Builder details</p>
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
                <th scope="col" class="py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-3">NAME</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">EMAIL</th>
                 <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">PHONENUMBER</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">ESTABLISHED YEAR</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">LOGO</th>
                  <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">TAG LINE</th>
                <th scope="col" class="px-3 py-3.5 text-left text-sm font-semibold text-gray-900">ACTIVE</th>
                <th scope="col" class="relative py-3.5 pl-3 pr-4 sm:pr-3">
                  <span class="sr-only">Delete</span>
                </th>
              </tr>
            </thead>
            <tbody class="bg-white"> 
              <tr v-for="(item, itemIdx) in builders" :key="item.uid" :class="itemIdx % 2 === 0 ? undefined : 'bg-gray-50'"  >
                <td class="whitespace-nowrap py-4 pl-4 pr-3 text-sm font-medium text-gray-900 sm:pl-3">{{ item.name }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ item.email }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ item.phone_number }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ item.established_year }}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ item.logo}}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500">{{ item.tag_line}}</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500" v-if="item.is_active">Active</td>
                <td class="whitespace-nowrap px-3 py-4 text-sm text-gray-500" v-if="!item.is_active">Not Active</td>
                 <td class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-3"  @click="emit('edit',item)">
                  <a href="#" class="text-indigo-600 hover:text-indigo-900"
                    >Edit<span class="sr-only">, {{ item.name }}</span></a 
                  >
                </td>
                <td class="relative whitespace-nowrap py-4 pl-3 pr-4 text-right text-sm font-medium sm:pr-3" @click="emit('delete',item.uid,itemIdx)">
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
  </div>
</template>

<script setup lang="ts">
import {ref,defineEmits,defineProps} from "vue"
const props=defineProps({
  builders:Object
})
// Define emits
const emit = defineEmits(["add","edit","delete"]);
</script>
