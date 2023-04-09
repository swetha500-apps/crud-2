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
                      <DialogTitle class="text-base font-semibold leading-6 text-white">Add Builder</DialogTitle>
                      <div class="ml-3 flex h-7 items-center">
                        <button type="button" class="rounded-md bg-indigo-700 text-indigo-200 hover:text-white focus:outline-none focus:ring-2 focus:ring-white" @click="open = false">
                          <span class="sr-only">Close panel</span>
                          <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                        </button>
                      </div>
                    </div>
                    <div class="mt-1">
                      <p class="text-sm text-indigo-300"></p>
                    </div>
                  </div>
                  <form>
                  <div class="relative flex-1 px-4 py-6 sm:px-6">        
                    <!-- input feild for name -->
    <label for="name" class="block text-sm font-medium leading-6 text-gray-900">NAME</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.name" type="text"  id="name" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="NAME" />
    </div>
                     <!-- input feild for email -->
    <label for="email" class="block text-sm font-medium leading-6 text-gray-900 mt-2">EMAIL</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.email" type="text"  id="email" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="EMAIL" />
    </div>
      <!-- input feild for phone_number -->
     <label for="phone_number" class="block text-sm font-medium leading-6 text-gray-900 mt-2">PHONE NUMBER</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.phone_number" type="text"  id="phone_number" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="PHONE NUMBER" />
    </div>
      <!-- input feild for established_year --> 
     <label for="established_year" class="block text-sm font-medium leading-6 text-gray-900 mt-2">ESTABLISHED YEAR</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.established_year" type="text"  id="established_year" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="ESTABLISHED YEAR" />
    </div>
     <!-- input feild for logo --> 
     <label for="logo" class="block text-sm font-medium leading-6 text-gray-900 mt-2">LOGO</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.logo" type="text"  id="logo" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="LOGO" />
    </div>
     <!-- input feild for tag_line --> 
     <label for="tag_line" class="block text-sm font-medium leading-6 text-gray-900 mt-2">TAG LINE</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.tag_line" type="text"  id="tag_line" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="TAG LINE" />
    </div>
  
    <!-- toggle button for active -->
  <SwitchGroup as="div" class="flex items-center mt-3">
    <Switch v-model="editPrefilledData.is_active" :class="[editPrefilledData.is_active ? 'bg-indigo-600' : 'bg-gray-200', 'relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2']">
      <span aria-hidden="true" :class="[editPrefilledData.is_active ? 'translate-x-5' : 'translate-x-0', 'pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out']" />
    </Switch>
    <SwitchLabel as="span" class="ml-3 text-sm">
      <span class="font-medium text-gray-900">Active</span>
    </SwitchLabel>
  </SwitchGroup>
  <!-- buttons for save and cancel -->
  <div class="flex flex-row float-right mt-5">
     <button type="button" class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3" @click="open=false">Cancel</button>
 <button type="button" class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="saved">Save</button>
  </div>
                  </div>
                  </form>
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
import { ref,defineEmits,defineProps } from 'vue'
import { Dialog, DialogPanel, DialogTitle, TransitionChild, TransitionRoot,Switch,SwitchGroup, SwitchLabel,Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { XMarkIcon } from '@heroicons/vue/24/outline'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
// Define emits
const emit=defineEmits(["saved"])
const props=defineProps({
    editPrefilledData:Object
})
const open = ref(true)
const saved=()=>{
 emit("saved",props.editPrefilledData)
 open.value=false
}

</script>