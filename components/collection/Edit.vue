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
                        >Panel title</DialogTitle
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
                        Lorem, ipsum dolor sit amet consectetur adipisicing elit
                        aliquam ad hic recusandae soluta.
                      </p>
                    </div>
                  </div>
                  <div class="relative flex-1 px-4 py-6 sm:px-6">
                    <div class="mt-1">
                      <p class="text-sm text-indigo-300">
                        Lorem, ipsum dolor sit amet consectetur adipisicing elit
                        aliquam ad hic recusandae soluta.
                      </p>
                    </div>

                    <div class="relative flex-1 px-4 py-6 sm:px-6">
                      <div class="mb-3">
                        <label
                          for="name"
                          class="block text-sm font-medium leading-6 text-gray-900"
                          >Name</label
                        >
                        <input
                          v-model="name"
                          type="text"
                          name="email"
                          id="name"
                          class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        />

                        <div class="mb-3">
                          <label
                            for="listname"
                            class="block text-sm font-medium leading-6 text-gray-900"
                            >ListName</label
                          >

                          <input
                            v-model="listName"
                            type="text"
                            name="email"
                            id="listname"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <div class="mb-3">
                          <label
                            for="details"
                            class="block text-sm font-medium leading-6 text-gray-900"
                            >Details</label
                          >

                          <input
                            v-model="details"
                            type="text"
                            name="email"
                            id="details"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <div class="mb-3">
                          <label
                            for="specifications"
                            class="block text-sm font-medium leading-6 text-gray-900"
                            >Specifications</label
                          >

                          <input
                            v-model="specifications"
                            type="text"
                            name="email"
                            id="specifications"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <div class="mb-3">
                          <label
                            for="projectAge"
                            class="block text-sm font-medium leading-6 text-gray-900"
                            >ProjectAge</label
                          >

                          <input
                            v-model="projectAge"
                            type="text"
                            name="email"
                            id="projectAge"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <div class="mb-3">
                          <label
                            for="logo"
                            class="block text-sm font-medium leading-6 text-gray-900"
                            >Logo</label
                          >

                          <input
                            v-model="logo"
                            type="text"
                            name="email"
                            id="logo"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                          />
                        </div>
                        <div class="mb-3">
                          <label
                            for="defaultImage"
                            class="block text-sm font-medium leading-6 text-gray-900"
                            >DefaultImage
                          </label>

                          <input
                            v-model="defaultImage"
                            type="text"
                            name="email"
                            id="defaultImage"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                          />
                        </div>

                        <button
                          type="button"
                          class="float-right mt-3 rounded-md bg-indigo-600 px-3.5 py-2.5 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                          @click="putData"
                        >
                          Save
                        </button>
                      </div>
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

<script setup>
import { ref } from "vue";
import {
  Dialog,
  DialogPanel,
  DialogTitle,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { XMarkIcon } from "@heroicons/vue/24/outline";
const open = ref(true);
const name = ref("");
const listName = ref("");
const details = ref("");
const specifications = ref("");
const projectAge = ref("");
const logo = ref("");
const defaultImage = ref("");
const props = defineProps({
  name: {
    type: String,
  },
  listName: {
    type: String,
  },
  details: {
    type: String,
  },
  specifications: {
    type: String,
  },
  projectAge: {
    type: String,
  },
  logo: {
    type: String,
  },
  defaultImage: {
    type: String,
  },
});
const emit=defineEmits(["putData"])
name.value = props.name;
listName.value = props.listName;
details.value = props.details;
specifications.value = props.specifications;
projectAge.value = props.projectAge;
logo.value = props.logo;
defaultImage.value = props.defaultImage;
const putData()=>{
  emit("putData",{
  name = name.value ,
  listName = listName.value,
  details =details.value ,
  specifications = specifications.value,
  projectAge = projectAge.value,
  logo =logo.value,
  defaultImage = defaultImage.value 
  })
}
</script>
