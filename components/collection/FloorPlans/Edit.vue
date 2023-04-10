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
                  <!-- input feild for floorname to edit-->
    <label for="floorName" class="block text-sm font-medium leading-6 text-gray-900">NAME</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.name" type="text"  id="floorName" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="NAME" />
    </div>
                  <!-- input feild for buildup area to edit-->
    <label for="buildUpArea" class="block text-sm font-medium leading-6 text-gray-900">BUILDUP AREA</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.build_up_area" type="number"  id="buildUpArea" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="BUILDUP AREA" />
    </div>
                <!-- input feild for carpetArea to edit-->
    <label for="carpetArea" class="block text-sm font-medium leading-6 text-gray-900">CARPET AREA</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.carpet_area" type="number"  id="carpetArea" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="CARPET AREA" />
    </div>
              <!-- input feild for metricArea to edit-->
    <label for="metricArea" class="block text-sm font-medium leading-6 text-gray-900">METRIC NAME</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.metric_name" type="text"  id="metricArea" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="METRIC NAME" />
    </div>
          <!-- input feild for facing to edit-->
    <label for="facing" class="block text-sm font-medium leading-6 text-gray-900">FACING</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.facing" type="text"  id="facing" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="FACING" />
    </div>
        <!-- input feild for bedrooms to edit-->
    <label for="bedrooms" class="block text-sm font-medium leading-6 text-gray-900">BEDROOMS</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.bedrooms" type="number"  id="bedrooms" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="BEDROOMS" />
    </div>
       <!-- input feild for bathrooms to edit-->
    <label for="bathrooms" class="block text-sm font-medium leading-6 text-gray-900">BATHROOMS</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.bathrooms" type="number"  id="bathrooms" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="BATHROOMS" />
    </div>
      <!-- input feild for kitchens to edit-->
    <label for="kitchens" class="block text-sm font-medium leading-6 text-gray-900">KITCHENS</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.kitchens" type="number"  id="kitchens" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="KITCHENS" />
    </div>
     <!-- input feild for balconies to edit-->
    <label for="balconies" class="block text-sm font-medium leading-6 text-gray-900">BALCONIES</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.balconies" type="number"  id="balconies" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="BALCONIES" />
    </div>
     <!-- input feild for project id to edit -->
    <label for="projectId" class="block text-sm font-medium leading-6 text-gray-900">PROJECT Id</label>
    <div class="mt-2">
      <input v-model="editPrefilledData.project_id" type="number"  id="projectId" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="PROJECT ID" />
    </div>
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