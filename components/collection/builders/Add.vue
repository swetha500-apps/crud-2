<template>
  <TransitionRoot as="template" :show="open">
    <Dialog as="div" class="relative z-10" @close="open = false">
      <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0" enter-to="opacity-100" leave="ease-in duration-200" leave-from="opacity-100" leave-to="opacity-0">
        <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" />
      </TransitionChild>

      <div class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex min-h-full items-end justify-center p-4 text-center sm:items-center sm:p-0">
          <TransitionChild as="template" enter="ease-out duration-300" enter-from="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95" enter-to="opacity-100 translate-y-0 sm:scale-100" leave="ease-in duration-200" leave-from="opacity-100 translate-y-0 sm:scale-100" leave-to="opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95">
            <DialogPanel class="relative transform overflow-hidden rounded-lg bg-white px-4 pb-4 pt-5 text-left shadow-xl transition-all sm:my-8 sm:w-full sm:max-w-lg sm:p-6">
              <div>
                <div class="mx-auto flex h-12 w-12 items-center justify-center rounded-full bg-green-100">
                  <CheckIcon class="h-6 w-6 text-green-600" aria-hidden="true" />
                </div>
                <div class="mt-3 text-center sm:mt-5">
                  <DialogTitle as="h3" class="text-base font-semibold leading-6 text-gray-900">Add Employee</DialogTitle>
                  <div class="mt-2">
                                <!-- input feild for name --> 
    <div class="flex flex-row mb-3">
       <label for="name" class="block text-sm font-medium leading-6 text-gray-900  mr-5 mt-3 ">NAME</label>
    <div class="mt-2">
      <input v-model="employeeDetails.name" type="text"  id="name" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="name" />
    </div>
    </div>
                           <!-- input feild for age --> 
    <div class="flex flex-row mb-3">
       <label for="age" class="block text-sm font-medium leading-6 text-gray-900 mt-3 mr-5 ml-3">AGE</label>
    <div class="mt-2">
      <input v-model="employeeDetails.age" type="number"  id="age" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="age" />
    </div>
    </div>
       <!-- input feild for gender -->
          <div class="flex flex-row mb-3">
     <label for="type" class=" block text-sm font-medium leading-6 text-gray-900 mt-3 ml-3">GENDER</label>
 <select
                            v-model="employeeDetails.gender"
                            class="bg-white block mb-3 px-3 rounded-md border-0 py-3 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 ml-3"
                         
                          >
                            <option value='' selected  >Please select a type</option>
                            <option value="MALE" >MALE</option>
                            <option value="FEMALE">FEMALE</option>
                          
                          
                          </select>
                          </div>
                           <!-- input feild for date of joining --> 
    <div class="flex flex-row mb-3">
       <label for="doj" class="block text-sm font-medium leading-6 text-gray-900 mt-2 mr-5 ml-3">DATE OF JOINING</label>
    <div class="mt-2">
      <input v-model="employeeDetails.doj" type="date"  id="doj" class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6 pl-3" placeholder="date of joining" />
    </div>
    </div>
      <!-- input feild for designation -->
      <div class="flex flex-row mb-3">
     <label for="type" class=" block text-sm font-medium leading-6 text-gray-900 mt-3 ml-3">DESIGNATION</label>
 <select
                            v-model="employeeDetails.designation"
                            class="bg-white block mb-3 px-3 rounded-md border-0 py-3 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-300 sm:text-sm sm:leading-6 ml-3"
                         
                          >
                            <option value='' selected  >Please select a type</option>
                            <option value="MANAGER" >MANAGER</option>
                            <option value="TL">TL</option>
                             <option value="EMPLOYEE">EMPLOYEE</option>
                          </select>
                          </div>
                  </div>
                </div>
              </div>
              <div class="mt-5 sm:mt-6 sm:grid sm:grid-flow-row-dense sm:grid-cols-2 sm:gap-3">
                <button type="button" class="inline-flex w-full justify-center rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 sm:col-start-2" @click="save">save</button>
                <button type="button" class="mt-3 inline-flex w-full justify-center rounded-md bg-white px-3 py-2 text-sm font-semibold text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 hover:bg-gray-50 sm:col-start-1 sm:mt-0" @click="open = false" ref="cancelButtonRef" >Cancel</button>
              </div> 
            </DialogPanel>
          </TransitionChild>
        </div>
      </div>
    </Dialog>
  </TransitionRoot>
</template>

<script setup lang="ts">
import { ref,defineEmits } from 'vue'
import { Dialog, DialogPanel, DialogTitle, TransitionChild, TransitionRoot } from '@headlessui/vue'
import { CheckIcon } from '@heroicons/vue/24/outline'
const emit=defineEmits(["save"])
const employeeDetails=ref({})
const open = ref(true)
const save=()=>{
  open.value = false
  emit('save',employeeDetails.value)
}
</script>