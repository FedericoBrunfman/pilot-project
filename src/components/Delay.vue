<template>
  <div class="flex flex-col items-center justify-between container">
    <div class="flex flex-col items-center">
      <h1 class="text-lg font-semibold">Time Delay</h1>
      <h3 class="self-start mt-4 text-gray-500 text-sm font-semibold">
        Set Time Delay For:
      </h3>
      <div class="flex self-start mt-4">
        <div
          class="w-8 border border-gray-300 flex items-center justify-center rounded-md p-4 text-gray-500 cursor-pointer relative"
        >
          <input type="number" ref="dayInputSelected" />
        </div>
        <div
          class="select-box rounded-md ml-4 flex items-center justify-between cursor-pointer relative"
        >
          <span class="text-xs text-gray-400 ml-3">{{ selected }}</span>
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="12"
            height="12"
            fill="currentColor"
            class="bi bi-chevron-down mr-2"
            viewBox="0 0 16 16"
            @click="showOptions = !showOptions"
          >
            <path
              fill-rule="evenodd"
              d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"
            />
          </svg>
          <div class="absolute options" v-if="showOptions">
            <div
              class="text-xs text-gray-400 my-1 hover:bg-gray-300 p-1"
              v-for="item in items"
              :key="item"
              @click="selected = item.name"
            >
              {{ item.name }}
            </div>
          </div>
        </div>
      </div>
      <div class="h-0.5 w-60 bg-gray-300 my-6 mr-4" />
      <h3 class="self-start text-gray-500 text-sm font-semibold">
        Refinements
      </h3>
      <div class="flex items-center justify-center mt-2">
        <input type="checkbox" id="cbox1" value="first_checkbox" />
        <div class="text-gray-400 text-xs ml-3">
          Delay until specific day(s) of the week
        </div>
      </div>
      <div class="flex">
        <button
          class="button-day self-start bg-transparent text-gray-700 font-semibold py-2 px-2 border border-gray-400 rounded mx-1 flex justify-center my-2"
          v-for="day in days"
          :class="{
            'bg-blue-500': setStyle(day),
            'text-gray-100': setStyle(day),
          }"
          :key="day"
          @click="addDay(day)"
        >
          {{ day.name }}
        </button>
      </div>
    </div>
    <div class="flex">
      <button
        class="text-xs w-20 bg-transparent text-blue-700 font-semibold py-2 px-2 border border-blue-400 rounded mx-2 flex justify-center my-2"
        @click="close"
      >
        Cancel
      </button>
      <button
        class="text-xs w-20 bg-blue-700 text-white font-semibold py-2 px-2 border rounded mx-2 flex justify-center my-2"
        @click="close"
      >
        Save
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: "- Select -",
      daySelected: [],
      showOptions: false,
      items: [
        {
          name: "Immediatly",
        },
        {
          name: "Hours",
        },
        {
          name: "Days",
        },
        {
          name: "Weeks",
        },
      ],
      days: [
        {
          name: "Mon",
          full: "Monday",
          order: 1,
        },
        {
          name: "Tues",
          full: "Tuesday",
          order: 2,
        },
        {
          name: "Weds",
          full: "Wesdnesday",
          order: 3,
        },
        {
          name: "Thurs",
          full: "Thursday",
          order: 4,
        },
        {
          name: "Fri",
          full: "Friday",
          order: 5,
        },
        {
          name: "Sat",
          full: "Saturday",
          order: 6,
        },
        {
          name: "Sun",
          full: "Sunday",
          order: 7,
        },
      ],
    };
  },
  methods: {
    addDay(day) {
      const index = this.daySelected.findIndex((d) => d?.order === day?.order);
      if (index !== -1) {
        delete this.daySelected[index];
      } else {
        this.daySelected.push(day);
      }
    },
    setStyle(day) {
      const index = this.daySelected.findIndex((d) => d?.order === day?.order);
      return index !== -1 ? true : false;
    },
    close() {
      const sortedDays = this.daySelected.sort((a, b) =>
        a.order > b.order ? 1 : -1
      );
      const obj = {
        day: this.$refs.dayInputSelected.value,
        time: this.selected,
        range: [sortedDays[0], sortedDays[sortedDays.length - 1]],
      };
      this.$emit("close", obj);
    },
  },
};
</script>

<style lang="css" scoped>
input[type="number"] {
  position: absolute;
  left: 10px;
  width: 21px;
  font-size: 14px;
  -moz-appearance: textfield;
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}
.select-box {
  width: 190px;
  border: 1px solid rgb(182, 182, 182);
}
.options {
  border: 1px solid rgb(182, 182, 182);
  width: 189px;
  top: 30px;
  z-index: 2;
  border-radius: 4px;
  background: white;
}
.button-day {
  width: 40px;
  font-size: 10px;
}
.container {
  height: 100%;
}
</style>
