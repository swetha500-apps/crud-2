<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-10" @close="open = false">
      <div class="fixed inset-0" />
      <div class="fixed inset-0 overflow-hidden">
        <div class="absolute inset-0 overflow-hidden">
          <div class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10">
            <TransitionChild as="template" enter="transform transition ease-in-out duration-500 sm:duration-700" enter-from="translate-x-full" enter-to="translate-x-0" leave="transform transition ease-in-out duration-500 sm:duration-700" leave-from="translate-x-0" leave-to="translate-x-full">
              <DialogPanel class="pointer-events-auto w-screen max-w-md">
                <div class="flex h-full flex-col overflow-y-scroll bg-white shadow-xl">
                  <div class="bg-indigo-700 px-4 py-6 sm:px-6">
                    <div class="flex items-center justify-between">
                      <DialogTitle class="text-base font-semibold leading-6 text-white">Add </DialogTitle>
                      <div class="ml-3 flex h-7 items-center">
                        <button type="button" class="rounded-md bg-indigo-700 text-indigo-200 hover:text-white focus:outline-none focus:ring-2 focus:ring-white" @click="open = false">
                          <span class="sr-only">Close panel</span>
                          <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                        </button>
                      </div>
                    </div>
                    <div class="mt-1">
                      <p class="text-sm text-indigo-300">Set a question,add questions and answers</p>
                    </div>
                  </div>
               
                  <div class="relative flex-1 px-4 py-6 sm:px-6">
                        <div>
                          <!-- input feild for category -->
     <label for="category" class="block text-sm font-medium leading-6 text-gray-900">Category </label>
    <div class="mt-2">
      <input type="text" id="category" v-model="form.category" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
 <!-- input feild for skill -->
     <label for="skill" class="block text-sm font-medium leading-6 text-gray-900">Skill</label>
    <div class="mt-2">
      <input type="text" id="skill" v-model="form.skill" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for question -->
     <label for="question" class="block text-sm font-medium leading-6 text-gray-900">Question</label>
    <div class="mt-2">
      <input type="text" id="question" v-model="form.question" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for answer -->
     <label for="answer" class="block text-sm font-medium leading-6 text-gray-900">Answer</label>
    <div class="mt-2">
      <input type="text" id="answer" v-model="form.answer" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for subskill -->
      <label for="sub_skill" class="block text-sm font-medium leading-6 text-gray-900">SubSkill</label>
    <div class="mt-2">
      <input type="text" id="sub_skill" v-model="form.sub_skill" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for questionurl -->
      <label for="question_url" class="block text-sm font-medium leading-6 text-gray-900">QuestionURL </label>
    <div class="mt-2">
      <input type="text" id="" v-model="form.question_url" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for answerhint -->
      <label for="answer_hint" class="block text-sm font-medium leading-6 text-gray-900"> Answer Hint</label>
    <div class="mt-2">
      <input type="text" id="answer_hint" v-model="form.answer_hint" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for explanation -->
        <label for="explanation" class="block text-sm font-medium leading-6 text-gray-900">Explanation</label>
    <div class="mt-2">
      <input type="text" id="explanation" v-model="form.explanation" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div> 
     <!-- input feild for marks -->
      <label for="marks" class="block text-sm font-medium leading-6 text-gray-900">Marks</label>
    <div class="mt-2">
      <input type="number" id="marks" v-model="form.marks" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="" />
    </div>         
      </div>
       <!-- buttons for save and cancel -->
       <div class="flex flex-row float-right mt-5">
     <button type="button" class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3" @click="open=false">Cancel</button>
 <button type="button" class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="save">Save</button>
  </div>
          </div>
                </div>
              </DialogPanel>
            </TransitionChild>
          </div>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup lang="ts">
import { ref,defineEmits } from 'vue'
import { Dialog, DialogPanel, DialogTitle, TransitionChild, TransitionRoot,Switch,SwitchGroup, SwitchLabel,Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { XMarkIcon } from '@heroicons/vue/24/outline'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
// Define emits
const emit = defineEmits(["save"]);
const open = ref(true)
const form:any = ref({});
const save=()=>{
 emit("save",form.value)
 open.value=false
}
</script>