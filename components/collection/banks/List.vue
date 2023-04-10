<template>
  <div class="px-4 sm:px-6 lg:px-8">
    <div class="sm:flex sm:items-center">
      <div class="sm:flex-auto">
        <h1 class="text-base font-semibold leading-6 text-gray-900">Question Banks</h1>
        <p class="mt-2 text-sm text-gray-700">Add questions and answers in bulk</p>
      </div>
      <div class="mt-4 sm:ml-16 sm:mt-0 sm:flex-none">
        <button type="button" class="block rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="emit('add')">Add Question</button>
      </div>
    </div>
    <div class="mt-8 flow-root">
      <div class="-mx-4 -my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
        <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
          <table class="min-w-full divide-y divide-gray-300">
            <thead>
              <tr>
                <th scope="col" class="whitespace-nowrap py-3.5 pl-4 pr-3 text-left text-sm font-semibold text-gray-900 sm:pl-0">ID</th>
                  <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Category</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Skill</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Question</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Answer</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">SubSkill</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">QuestionURL</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Answer Hint</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Explanation</th>
                <th scope="col" class="whitespace-nowrap px-2 py-3.5 text-left text-sm font-semibold text-gray-900">Marks</th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200 bg-white">
              <tr v-for="question in questions" :key="question">
                 <td class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0">{{ question.id }}</td>
                <td class="whitespace-nowrap py-2 pl-4 pr-3 text-sm text-gray-500 sm:pl-0">{{ question.category }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm font-medium text-gray-900">{{ question.skill }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-900">{{ question.question }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ question.answer }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ question.sub_skill }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ question.question_url }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ question.answer_hint }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ question.explanation }}</td>
                <td class="whitespace-nowrap px-2 py-2 text-sm text-gray-500">{{ question.marks }}</td>
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
  questions:Array
})
// Define emits
const emit = defineEmits(["add"]);
</script>