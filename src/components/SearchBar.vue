<template>
  <div class="container flex mx-auto relative">
    <div class="flex border-2 rounded">
      <button class="flex items-center justify-center px-4">
        <svg
          class="w-6 h-6"
          fill="currentColor"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
        >
          <path
            d="M16.32 14.9l5.39 5.4a1 1 0 0 1-1.42 1.4l-5.38-5.38a8 8 0 1 1 1.41-1.41zM10 16a6 6 0 1 0 0-12 6 6 0 0 0 0 12z"
          ></path>
        </svg>
      </button>
      <input
        @click="this.isToggled = !this.isToggled"
        type="text"
        class="search-input px-2 py-1 w-60"
        placeholder="Search"
      />
    </div>
    <div
      class="results p-4 container flex mx-auto border-2 rounded shadow absolute top-10 z-1 bg-white"
      v-if="isToggled"
    >
      <div class="flex">
        <div class="lines">
          <div class="gray-line h-2 w-40 bg-gray-300 m-2" />
          <div class="gray-line h-2 w-40 bg-gray-300 m-2" />
          <div class="gray-line h-2 w-20 bg-gray-300 m-2" />
        </div>
        <div class="circle ml-5 mt-1" />
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  name: "SearchBar",
  setup() {
    const isToggled = ref(false)

    return {
      isToggled
    }
  }
};
</script>

<style lang="css" scoped>
::placeholder {
  color: black;
}
.results {
  width: 300px;
}
.circle {
  background: gray;
  height: 45px;
  width: 45px;
  border-radius: 50%;
}
</style>
