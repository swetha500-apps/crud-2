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
                      <DialogTitle class="text-base font-semibold leading-6 text-white">Add Custom Field</DialogTitle>
                      <div class="ml-3 flex h-7 items-center">
                        <button type="button" class="rounded-md bg-indigo-700 text-indigo-200 hover:text-white focus:outline-none focus:ring-2 focus:ring-white" @click="open = false">
                          <span class="sr-only">Close panel</span>
                          <XMarkIcon class="h-6 w-6" aria-hidden="true" />
                        </button>
                      </div>
                    </div>
                    <div class="mt-1">
                      <p class="text-sm text-indigo-300">Set a label,select custom field type and edit</p>
                    </div>
                  </div>
                  <form>
                  <div class="relative flex-1 px-4 py-6 sm:px-6">
                    <!-- input feild for label -->
    <label for="label" class="block text-sm font-medium leading-6 text-gray-900">Label</label>
    <div class="mt-2">
      <input v-model="form.name" type="text"  id="label" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="Label" />
    </div>
                     <!-- input feild for description -->
    <label for="description" class="block text-sm font-medium leading-6 text-gray-900 mt-2">Description</label>
    <div class="mt-2">
      <input v-model="form.type_data.description" type="text"  id="description" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="Description" />
    </div>
      <!-- input feild for type -->
     <label for="type" class=" block text-sm font-medium leading-6 text-gray-900 mt-2">Type</label>
 <select
                            v-model="form.type"
                            class="bg-white block mb-3 px-3 rounded-md border-0 py-3 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 w-[100%]"
                         
                          >
                            <option value='' selected  >Please select a type</option>
                            <option value="TEXTBOX" >TEXTBOX</option>
                            <option value="RADIO_BUTTONS">RADIOBUTTONS</option>
                            <option value="MULTI_CHECKBOX">
                              MULTICHECKBOX
                            </option>
                          
                          </select>
      <!-- input feild for placeholder --> 
     <label for="placeholder" class="block text-sm font-medium leading-6 text-gray-900 mt-2">Placeholder</label>
    <div class="mt-2">
      <input v-model="form.type_data.placeholder" type="text"  id="placeholder" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="placeholder" />
    </div>
    <!-- toggle button for mandatory -->
  <SwitchGroup as="div" class="flex items-center mt-3">
    <Switch v-model="form.type_data.is_required" :class="[form.type_data.is_required ? 'bg-indigo-600' : 'bg-gray-200', 'relative inline-flex h-6 w-11 flex-shrink-0 cursor-pointer rounded-full border-2 border-transparent transition-colors duration-200 ease-in-out focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2']">
      <span aria-hidden="true" :class="[form.type_data.is_required ? 'translate-x-5' : 'translate-x-0', 'pointer-events-none inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out']" />
    </Switch>
    <SwitchLabel as="span" class="ml-3 text-sm">
      <span class="font-medium text-gray-900">Mandatory</span>
    </SwitchLabel>
  </SwitchGroup>
  <div class="flex flex-row float-right mt-5">
     <button type="button" class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 mr-3" @click="open=false">Cancel</button>
 <button type="button" class="rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600" @click="save">Save</button>
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
import { ref,defineEmits } from 'vue'
import { Dialog, DialogPanel, DialogTitle, TransitionChild, TransitionRoot,Switch,SwitchGroup, SwitchLabel,Menu, MenuButton, MenuItem, MenuItems } from '@headlessui/vue'
import { XMarkIcon } from '@heroicons/vue/24/outline'
import { ChevronDownIcon } from '@heroicons/vue/20/solid'
// Define emits
const emit=defineEmits(["save"])
const form:any = ref({type_data:{}});
const open = ref(true)
const save=()=>{
 emit("save",form.value)
 open.value=false
}

</script>