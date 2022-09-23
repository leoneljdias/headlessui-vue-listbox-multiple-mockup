<template>
  <ListboxLabel class="h-5 w-5 text-gray-400">MultiSelect:</ListboxLabel>
  <Listbox as="div" v-model="selectedOption" v-slot="{ open }" multiple>
    <div class="relative">
      <span class="inline-block w-full rounded-md shadow-sm">
        <ListboxButton
          class="relative w-full py-2 pl-3 pr-10 text-left transition duration-150 ease-in-out bg-white border border-gray-300 rounded-md cursor-default focus:outline-none focus:shadow-outline-blue focus:border-blue-300 sm:text-sm sm:leading-5"
        >
          <span
            class="block truncate"
            :class="selectedOption.length === 0 ? 'text-gray-400' : ''"
            >{{
              selectedOption.length === 0
                ? "Please select a option"
                : selectedOption.map((x) => x.name).join(", ")
            }}</span
          >
          <span
            class="pointer-events-none absolute inset-y-0 right-0 ml-3 flex items-center pr-2"
          >
            <ChevronUpDownIcon
              class="h-5 w-5 text-gray-400"
              aria-hidden="true"
            />
          </span>
        </ListboxButton>
      </span>
      <transition
        leave-active-class="transition duration-100 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
        v-if="open"
      >
        <div class="absolute w-full mt-1 bg-white rounded-md shadow-lg">
          <ListboxOptions
            class="py-1 overflow-auto text-base leading-6 rounded-md shadow-xs max-h-60 space-y-px pl-px focus:outline-none sm:text-sm sm:leading-5"
            static="static"
          >
            <ListboxOption
              v-for="option in options"
              :key="option.id"
              :value="option"
              v-slot="{ selected, active }"
              @click="onClick"
            >
              <div
                class="mr-px"
                :class="`${
                  selected && active
                    ? 'bg-gray-700 text-white'
                    : selected
                    ? 'bg-gray-200'
                    : active
                    ? 'text-white bg-blue-600'
                    : 'text-gray-900'
                } cursor-default select-none relative py-2 pl-2 pr-4`"
              >
                <span
                  :class="`${
                    selected ? 'font-semibold' : 'font-normal'
                  } block truncate text-left`"
                  >{{ option.name }}</span
                >
                <span
                  v-if="selected"
                  :class="[
                    active ? 'text-white' : 'text-indigo-600',
                    'absolute inset-y-0 right-0 flex items-center pr-4',
                  ]"
                >
                  <CheckIcon class="h-5 w-5" aria-hidden="true" />
                </span>
              </div>
            </ListboxOption>
          </ListboxOptions>
        </div>
      </transition>
    </div>
  </Listbox>
</template>

<script>
import {
  Listbox,
  ListboxButton,
  ListboxOption,
  ListboxOptions,
} from "@headlessui/vue";
import { CheckIcon, ChevronUpDownIcon } from "@heroicons/vue/24/solid";

export default {
  components: {
    Listbox,
    ListboxButton,
    ListboxOption,
    ListboxOptions,
    CheckIcon,
    ChevronUpDownIcon,
  },
  props: ["modelValue", "options"],
  emits: ["update:modelValue"],
  computed: {
    selectedOption: {
      get() {
        return this.modelValue;
      },
      set(newValue) {
        this.$emit("update:modelValue", newValue);
      },
    },
  },
};
</script>