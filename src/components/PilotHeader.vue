<template>
  <div class="pilot-header flex items-center justify-between border-b-2">
    <div class="flex items-center">
      <div class="logo w-60">
        <img src="./../assets/logo.jpeg" alt="" srcset="" />
      </div>
      <search-bar />
    </div>
    <div class="flex item-center mr-3">
      <div
        class="user relative flex items-center cursor-pointer"
        @click="showItems = !showItems"
      >
        <div class="initials mr-4">
          <div class="initial">B</div>
        </div>
        <div class="user-name text-xs">
          <span>Blositive.nl</span>
          <div class="menu absolute shadow z-30 bg-white" v-if="showItems">
            <div class="item flex items-center my-2 p-2">
              <div class="rounded-full bg-blue-700 w-7 h-7 mr-2" />
              <div class="item-text">Blositive.nl</div>
            </div>
            <div class="divider w-100 h-0.5 bg-gray-200" />
            <div class="item flex items-center my-2 p-2">
              <div class="rounded-full bg-gray-500 w-7 h-7 mr-2" />
              <div class="item-text">Blositive.co.uk</div>
            </div>
            <div class="divider w-100 h-0.5 bg-gray-300" />
            <div class="item flex items-center my-2 p-2">
              <div class="rounded-full bg-gray-500 w-7 h-7 mr-2" />
              <div class="item-text">Blositive.de</div>
            </div>
            <div class="divider w-100 h-0.5 bg-gray-300" />
            <div class="item flex items-center my-2 p-2">
              <div
                class="rounded-full bg-gray-500 w-7 h-7 mr-2 flex items-center justify-center"
              >
                <span class="plus text-white text-3xl mb-1">+</span>
              </div>
              <div class="item-text">Add store</div>
            </div>
          </div>
        </div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="12"
          height="12"
          fill="currentColor"
          class="bi bi-chevron-down ml-4"
          viewBox="0 0 16 16"
        >
          <path
            fill-rule="evenodd"
            d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"
          />
        </svg>
      </div>
      <div class="h-7 w-0.5 bg-gray-200 mt-2 ml-2" />
      <div class="messages relative mt-1">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="36"
          height="36"
          class="envelope ml-4"
          viewBox="0 0 1792 1792"
        >
          <path
            d="M1664 1504v-768q-32 36-69 66-268 206-426 338-51 43-83 67t-86.5 48.5-102.5 24.5h-2q-48 0-102.5-24.5t-86.5-48.5-83-67q-158-132-426-338-37-30-69-66v768q0 13 9.5 22.5t22.5 9.5h1472q13 0 22.5-9.5t9.5-22.5zm0-1051v-24.5l-.5-13-3-12.5-5.5-9-9-7.5-14-2.5h-1472q-13 0-22.5 9.5t-9.5 22.5q0 168 147 284 193 152 401 317 6 5 35 29.5t46 37.5 44.5 31.5 50.5 27.5 43 9h2q20 0 43-9t50.5-27.5 44.5-31.5 46-37.5 35-29.5q208-165 401-317 54-43 100.5-115.5t46.5-131.5zm128-37v1088q0 66-47 113t-113 47h-1472q-66 0-113-47t-47-113v-1088q0-66 47-113t113-47h1472q66 0 113 47t47 113z"
          />
        </svg>
        <div class="absolute notificaiton rounded-full h-3 w-3 bg-blue-600" />
      </div>
      <div class="h-7 w-0.5 bg-gray-200 mt-2 ml-4" />
      <div class="customer flex align-center text-xs ml-2">
        <div class="avatar "><img  class="rounded-full" src="./../assets/avatar.jpeg" alt="" srcset=""></div>
        <div class="mt-3 ml-2">Customer</div>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="12"
          height="12"
          fill="currentColor"
          class="bi bi-chevron-down ml-2 mt-4"
          viewBox="0 0 16 16"
        >
          <path
            fill-rule="evenodd"
            d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "./SearchBar.vue";
import { ref } from "vue";
export default {
  name: "PilotHeader",
  setup() {
    const showItems = ref(false);

    return {
      showItems,
    };
  },
  components: {
    SearchBar,
  },
};
</script>

<style lang="css" scoped>
.pilot-header {
  font-size: 0.875rem;
}
.logo img {
  height: 6rem;
}
.initials {
  position: relative;
  width: 50px;
  height: 50px;
  border-radius: 100%;
  box-shadow: inset 0px 0px 0px 3px white;
  border: 2px dotted #159815;
}

.initials:before {
  position: absolute;
  content: "";
  bottom: -47px;
  left: -47px;
  width: 40px;
  height: 40px;
  margin: 50px;
  border-radius: 100%;
  box-shadow: inset 0px 0px 0px 3px white;
  border: 2px dotted #159815;
}

.initial {
  position: absolute;
  top: 12px;
  color: #159815;
  left: 19px;
  font-weight: 800;
}

.menu {
  left: 0px;
  width: 162px;
  top: 50px;
}

.envelope {
  fill: gray;
}

.notificaiton {
  top: 2px;
  left: 43px;
}

.avatar {
  height: 40px;
  width: 40px;
}
</style>
