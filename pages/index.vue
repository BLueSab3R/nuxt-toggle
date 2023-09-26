<template>
  <div class="flex flex-col items-center justify-center h-screen">
    <div class="bg-gray-200 rounded-md p-4">
      <select @change="optionHandler">
        <option value="null" disabled selected hidden>Choose option</option>
        <option value="simple">Simple toggle</option>
        <option value="short">Short toggle</option>
        <option value="icon">Toggle with icon</option>
      </select>
    </div>
    <ToggleButton @turn-on="turnOn" @turn-off="turnOff" :accept="accept">
      <button
        type="button"
        :class="{
          'bg-red-600': counter === 0,
          'bg-yellow-200': counter === 1,
          'bg-green-600': counter === 2,
          'w-11 h-6 rounded-full border-2 border-transparent': type === 'simple' || type === 'icon',
          'h-5 w-10 group items-center  transition-colors duration-200  ': type === 'short',
          'relative border-2 border-transparent transition-colors  duration-200 ease-in-out':
            type === 'icon',
        }"
        class="mt-5 inline-flex flex-shrink-0 cursor-pointer rounded-full focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
        role="switch"
        :aria-checked="!accept ? 'false' : 'true'"
      >
        <span
          v-if="type === 'simple' || type === 'short'"
          aria-hidden="true"
          :class="{
            'translate-x-0 duration-200 ease-in': counter === 0,
            'translate-x-2.5 duration-100 ease-in': counter === 1,
            'translate-x-5 duration-200 ease-in': counter === 2,
            'inline-block h-5 w-5 transform bg-white shadow ring-0 transition': type === 'simple',
            'absolute  inline-block h-5 w-5 transform rounded-full border border-gray-200 bg-white shadow ring-0 transition-transform duration-200 ease-in-out':
              type === 'short',
          }"
          class="pointer-events-none rounded-full transition-colors duration-200 ease-in-out"
        >
        </span>
        <span
          v-if="type === 'icon'"
          :class="{
            'translate-x-0 duration-200 ease-in': counter === 0,
            'translate-x-2.5 duration-100 ease-in': counter === 1,
            'translate-x-5 duration-200 ease-in': counter === 2,
          }"
          class="pointer-events-none relative inline-block h-5 w-5 transform rounded-full bg-white shadow ring-0 transition duration-200 ease-in-out"
        >
          <span
            :class="{
              'translate-x-0 duration-200 ease-in': counter === 0,
              'translate-x-0.4 duration-100 ease-in': counter === 1,
              'translate-x-0.7 duration-200 ease-in': counter === 2,
            }"
            class="opacity-100 duration-200 ease-in absolute inset-0 flex h-full w-full items-center justify-center transition-opacity"
            aria-hidden="true"
          >
            <svg class="h-3 w-3  text-gray-400" fill="none" viewBox="0 0 12 12">
              <path
                d="M4 8l2-2m0 0l2-2M6 6L4 4m2 2l2 2"
                stroke="currentColor"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </span>
        </span>
      </button>
    </ToggleButton>
  </div>
</template>

<script setup>
const type = ref(null);
const accept = ref(false);
let counter = ref(0);
const turnOn = () => {
  counter.value = 1;
  setTimeout(() => {
    counter.value = 2;
    accept.value = true;
  }, 1000);
};

const turnOff = () => {
  counter.value = 1;
  setTimeout(() => {
    counter.value = 0;
    accept.value = false;
  }, 1000);
};

const optionHandler = (event) => {
  type.value = event.target.value;
};
</script>
