<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-10" @close="open = false">
      <div class="fixed inset-0" />
      <div class="fixed inset-0 overflow-hidden">
        <div class="absolute inset-0 overflow-hidden">
          <div
            class="pointer-events-none fixed inset-y-0 right-0 flex max-w-full pl-10"
          >
            <TransitionChild
              as="template"
              enter="transform transition ease-in-out duration-500 sm:duration-700"
              enter-from="translate-x-full"
              enter-to="translate-x-0"
              leave="transform transition ease-in-out duration-500 sm:duration-700"
              leave-from="translate-x-0"
              leave-to="translate-x-full"
            >
              <DialogPanel class="pointer-events-auto w-screen max-w-md">
                <div
                  class="flex h-full flex-col overflow-y-scroll bg-white shadow-xl"
                >
                  <div class="bg-indigo-700 px-4 py-6 sm:px-6">
                    <div class="flex items-center justify-between">
                      <DialogTitle
                        class="text-base font-semibold leading-6 text-white"
                        >Add Test</DialogTitle
                      >
                      <div class="ml-3 flex h-7 items-center">
                        <button
                          type="button"
                          class="rounded-md bg-indigo-700 text-indigo-200 hover:text-white focus:outline-none focus:ring-2 focus:ring-white"
                          @click="open = false"
                        >
                          <span class="sr-only">Close panel</span>
                          <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                        </button>
                      </div>
                    </div>
                    <div class="mt-1">
                      <p class="text-sm text-indigo-300">
                        Set a exam,add questions
                      </p>
                    </div>
                  </div>
                  <div class="relative flex-1 px-4 py-6 sm:px-6">
                    <!-- INPUT FEILD FOR NAME AND TYPE -->

                    <label
                      for="name"
                      class="block text-sm font-medium leading-6 text-gray-900"
                      >Name</label
                    >
                    <div class="mt-2">
                      <input
                        type="text"
                        id="name"
                        v-model="form.name"
                        class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3"
                        placeholder="Name"
                      />
                    </div>

                    <label
                      for="type"
                      class="block text-sm font-medium leading-6 text-gray-900"
                      >Type</label
                    >
                    <div class="mt-2">
                      <input
                        type="text"
                        id="type"
                        v-model="form.type"
                        class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3"
                        placeholder="Type"
                      />
                    </div>

                    <!-- INPUT  FEILD FOR MAXTIMEALLOWED AND DUEDATE -->

                    <label
                      for="max_time_allowed"
                      class="block text-sm font-medium leading-6 text-gray-900"
                      >MAX TIME ALLOWED</label
                    >
                    <div class="mt-2">
                      <input
                        type="number"
                        id="max_time_allowed"
                        v-model="form.max_time_allowed"
                        class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3"
                        placeholder="IN MINS"
                      />
                    </div>

                    <label
                      for="due_date"
                      class="block text-sm font-medium leading-6 text-gray-900"
                      >DUE DATE</label
                    >
                    <div class="mt-2">
                      <input
                        type="text"
                        id="due_date"
                        v-model="form.due_date"
                        class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3"
                        placeholder="Type"
                      />
                    </div>


                    <!--INPUT FEILD FOR DIFFICULTY LEVEL -->
                    <label
                      for="difficulty_level"
                      class="block text-sm font-medium leading-6 text-gray-900 mt-2"
                      >LEVEL</label
                    >
                    <select
                      v-model="form.difficulty_level"
                      class="bg-white block mb-3 px-3 rounded-md border-0 py-3 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                    >
                      <option value="" selected>Please select a type</option>
                      <option value="Easy">Easy</option>
                      <option value="Medium">Medium</option>
                      <option value="Hard">Hard</option>
                    </select>
                    <!-- TOGGLE BUTTON FOR MULTIPLEATTEMPTS AND STATUS  -->
                    <div class="flex flex-row">
                 <div class="flex flex-row mr-5">
                   <Switch v-model="form.multiple_attempts_allowed" :class="[form.multiple_attempts_allowed ? 'bg-indigo-600' : 'bg-gray-200', 'relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2']">
    <span aria-hidden="true" :class="[form.multiple_attempts_allowed ? 'translate-x-5' : 'translate-x-0', 'pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out']" />
    
  </Switch>
  <h1>MULTIPLE TIMES ALLOWED</h1>
                   </div>
                     <div class="flex flex-row">
                   <Switch v-model="form.status" :class="[form.status ? 'bg-indigo-600' : 'bg-gray-200', 'relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2']">
    <span aria-hidden="true" :class="[form.status ? 'translate-x-5' : 'translate-x-0', 'pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out']" />
    
  </Switch>
  <h1>STATUS</h1>
                   </div>
                   </div>
                   <!-- TEXTAREA FOR DESCRIPTION -->
                    <label for="description" class="block text-sm font-medium leading-6 text-gray-900">DESCRIPTION</label>
    <div class="mt-2">
      <textarea v-model="form.description" rows="4" name="description" id="description" class="block w-full rounded-md border-0 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:py-1.5 sm:text-sm sm:leading-6" />
    </div>
                   <!-- SAVE AND EDIT BUTTONS -->
                    <div class="flex flex-row float-right mt-5">
                      <button
                        type="button"
                        class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3"
                        @click="open = false"
                      >
                        Cancel
                      </button>
                      <button
                        type="button"
                        class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                        @click="save"
                      >
                        Save
                      </button>
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
import { ref, defineEmits } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
  Switch,
  SwitchGroup,
  SwitchLabel,
  Menu,
  MenuButton,
  MenuItem,
  MenuItems,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";
import { ChevronDownIcon } from "@heroicons/vue/20/solid";
// Define emits
const emit = defineEmits(["save"]);
const open = ref(true);
const form: any = ref({});
const save = () => {
  emit("save", form.value);
  open.value = false;
};
</script>
