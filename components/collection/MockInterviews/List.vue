<template>
  <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">MOCK INTERVIEWS</h1>
        <p class="mt-2 text-sm text-gray-700">Add interviews and questions in bulk</p>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        <button type="button" class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="emit('add')">Add interview</button>
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th scope="col" class="whitespace-nowrap py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0">NAME</th>
                  <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">TYPE</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">MAXTIME</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">DUE DATE</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">DIFICULTY LEVEL</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">MULTIPLE ATTEMPTS </th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">STATUS</th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <tr v-for="interview in interviews" :key="interview">
                 <td class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0">{{ interview.name }}</td>
                <td class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0">{{ interview.type }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm font-medium text-gray-900">{{ interview.max_time_allowed }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-900">{{ interview.due_date }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ interview.difficulty_level }}</td>
                 <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500" v-if="interview.multiple_attempts_allowed==1">Allowed</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500" v-if="interview.multiple_attempts_allowed==0">Not allowed</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500" v-if="interview.status==0">Not completed</td>
                 <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500" v-if="interview.status==1">completed</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {ref,defineEmits,defineProps} from "vue"
const props=defineProps({
  interviews:Array
})
// Define emits
const emit = defineEmits(["add"]);
</script>