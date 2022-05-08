<template>
  <div class="automation-flow flex p-4">
    <div
      class="left bg-white p-4 rounded-lg shadow-md flex flex-col items-center"
    >
      <div v-if="noAction">
        <h2 class="text-lg font-semibold mb-4">Build your Flow</h2>
        <div class="self-start mt-2 mb-4">
          <span class="text-gray-500 font-semibold text-sm ml-4">Messages</span>
        </div>
        <draggable
          class="dragArea list-group"
          :list="messageItems"
          :group="{ name: 'items', pull: 'clone', put: false }"
          :clone="cloneItem"
          @start="isDragging = true"
          @end="isDragging = false"
          item-key="id"
        >
          <template #item="{ element }">
            <button
              class="text-xs bg-transparent text-gray-700 font-semibold py-2 px-2 border border-gray-400 rounded mx-2 flex justify-between my-2"
            >
              <div class="flex">
                <div class="envelope-icon bg-gray-300 rounded-full h-7 w-7">
                  <img
                    class="envelope"
                    v-if="element.name === 'Email'"
                    src="./../assets/envelope.svg"
                    alt=""
                  />
                  <img
                    class="message"
                    v-if="element.name === 'SMS'"
                    src="./../assets/message.svg"
                    alt=""
                  />
                </div>
                <div class="text-gray-400 ml-6 mt-1">{{ element.name }}</div>
              </div>
              <div class="drag-icon">
                <img src="./../assets/drag.svg" class="drag" alt="" srcset="" />
              </div>
            </button>
          </template>
        </draggable>
        <div class="h-0.5 w-80 bg-gray-200 my-6" />
        <div class="self-start mb-4">
          <span class="text-gray-500 font-semibold text-sm ml-4">Actions</span>
        </div>
        <draggable
          class="dragArea list-group"
          :list="actionItems"
          :group="{ name: 'items', pull: 'clone', put: false }"
          :clone="cloneItem"
          @start="isDragging = true"
          @end="isDragging = false"
          item-key="id"
        >
          <template #item="{ element }">
            <button
              class="text-xs bg-transparent text-gray-700 font-semibold py-2 px-2 border border-gray-400 rounded mx-2 flex justify-between my-2"
              :class="{
                'bg-blue-100': element.name === 'Conditional Split',
                'bg-gray-200': element.name === 'Delay',
                'bg-gray-300': element.name === 'A/B Test',
              }"
            >
              <div class="flex">
                <div class="envelope-icon bg-gray-300 rounded-full h-7 w-7">
                  <img
                    class="envelope mr-1"
                    v-if="element.name === 'Conditional Split'"
                    src="./../assets/direction.svg"
                    alt=""
                  />
                  <img
                    class="clock"
                    v-if="element.name === 'Delay'"
                    src="./../assets/clock.svg"
                    alt=""
                  />
                  <img
                    class="abtesting"
                    v-if="element.name === 'A/B Test'"
                    src="./../assets/ab-testing.svg"
                    alt=""
                  />
                </div>
                <div class="text-gray-400 ml-6 mt-1">{{ element.name }}</div>
              </div>
              <div class="drag-icon">
                <img src="./../assets/drag.svg" class="drag" alt="" srcset="" />
              </div>
            </button>
          </template>
        </draggable>
      </div>
      <delay @close="saveContent($event)" v-else />
    </div>
    <div class="right flex flex-col justify-start items-center">
      <draggable
        class="dragArea list-group"
        :list="rightItems"
        @change="chooseItem($event)"
        group="items"
        item-key="id"
      >
        <template #item="{ element }">
          <div class="flex flex-col justify-center items-center">
            <div
              class="list-group-item border border-gray-300 h-20 rounded-md flex p-1 items-center cursor-pointer shadow-lg"
              :class="{
                'bg-gray-400':
                  element.name === 'Trigger' || element.name === 'SMS',
                'bg-white': element.name === 'Email',
                'bg-blue-100': element.name === 'Conditional Split',
                'bg-gray-200': element.name === 'Delay',
                'bg-gray-300': element.name === 'A/B Test',
              }"
            >
              <div
                class="icon-container bg-white rounded-full w-7 h-7 relative ml-4"
                :class="{
                  'bg-white': element.name !== 'Email',
                  'bg-gray-400': element.name === 'Email',
                }"
              >
                <img
                  src="./../assets/thunder.svg"
                  class="icon-left absolute"
                  v-if="element.name === 'Trigger'"
                  alt=""
                  srcset=""
                />
                <img
                  src="./../assets/envelope.svg"
                  class="envelope"
                  v-if="element.name === 'Email'"
                  alt=""
                  srcset=""
                />
                <img
                  src="./../assets/message.svg"
                  class="message"
                  v-if="element.name === 'SMS'"
                  alt=""
                  srcset=""
                />
                <img
                  src="./../assets/direction.svg"
                  class="message"
                  v-if="element.name === 'Conditional Split'"
                  alt=""
                  srcset=""
                />
                <img
                  src="./../assets/clock.svg"
                  class="clock"
                  v-if="element.name === 'Delay'"
                  alt=""
                  srcset=""
                />
                <img
                  src="./../assets/ab-testing.svg"
                  class="clock"
                  v-if="element.name === 'A/B Test'"
                  alt=""
                  srcset=""
                />
              </div>
              <div class="ml-2 card">
                <div class="ml-1 text-xs text-gray-600">{{ element.name }}</div>
                <div class="ml-1 text-xs text-gray-600">{{ element.p1 }}</div>
                <div
                  class="ml-1 text-xs text-gray-600"
                  :class="{ 'underline font-semibold': element.id === 3 }"
                >
                  {{ element.p2 }}
                </div>
              </div>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="dots-icon"
                viewBox="0 0 256 256"
              >
                <rect fill="none" />
                <circle cx="128" cy="64" r="16" />
                <circle cx="128" cy="128" r="16" />
                <circle cx="128" cy="192" r="16" />
              </svg>
              <div></div>
            </div>
            <div class="w-0.5 h-20 bg-gray-300 relative">
              <div class="plus" v-if="isDragging">
                <span class="plus-text">+</span>
              </div>
              <div class="end-pointer" />
            </div>
          </div>
        </template>
      </draggable>
      <div class="flex items-center">
        <img src="./../assets/exit.svg" alt="" class="exit" srcset="" />
        <span class="text-sm text-gray-500">Exit</span>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import Delay from "./Delay.vue";
let idGlobal = 8;
export default {
  data() {
    return {
      messageItems: [
        {
          name: "Email",
          p1: "This is a test email text:",
          p2: '"This is a test email text"',
          id: 1,
        },
        {
          name: "SMS",
          p1: "This is a test SMS text:",
          p2: '"This is a test SMS text"',
          id: 2,
        },
      ],
      actionItems: [
        {
          name: "Conditional Split",
          p1: "This is a test split text:",
          p2: '"This is a test split text"',
          id: 3,
        },
        {
          name: "Delay",
          p1: "Two days and only proceed",
          p2: "Between Monday and Friday",
          id: 4,
        },
        {
          name: "A/B Test",
          p1: "This is a AB Testing text:",
          p2: '"This is a AB Testing text"',
          id: 5,
        },
      ],
      rightItems: [
        {
          name: "Trigger",
          p1: "When added to Audience:",
          p2: '"ZitGlobbler orders only"',
          id: 6,
        },
      ],
      drag: false,
      isDragging: false,
      noAction: true,
    };
  },
  components: {
    draggable,
    Delay,
  },
  methods: {
    cloneItem({ name, p1, p2 }) {
      return {
        id: idGlobal++,
        name: name,
        p1: p1,
        p2: p2,
      };
    },
    chooseItem({ added }) {
      const el = added?.element;
      if (el && el.name === "Delay") {
        this.noAction = false;
      }
    },
    saveContent(data) {
      const a = this.rightItems.filter((item) => item.name === 'Delay')[0]
      a.p1 = `${data.day} ${data.time} and only proceed`
      if (data.range[0]) {
        a.p2 = `Between ${data.range[0].full} and ${data.range[1].full}`
      } else {
        a.p2 = 'All days'
      }
      this.noAction = true;
    },
  },
};
</script>

<style lang="css" scoped>
.automation-flow {
  background-color: #e5e5f7;
  height: 100%;
  min-height: 80vh;
  background-image: linear-gradient(
      #e1e1e168 2.4000000000000004px,
      transparent 2.4000000000000004px
    ),
    linear-gradient(
      to right,
      #edebeb79 2.4000000000000004px,
      #ffffff9a 2.4000000000000004px
    );
  background-size: 90px 90px;
}
.left {
  width: 22rem;
}
.right {
  height: 100%;
  width: 100%;
}
.envelope {
  margin-left: 6px;
  margin-top: 5px;
  fill: #696969;
}
.message {
  margin-left: 2px;
  margin-top: 3px;
}
button {
  width: 18rem;
}
.drag {
  fill: #696969;
  margin-top: 1px;
}
.icon-left {
  left: 5px;
  top: 5px;
  width: 20px;
  z-index: 13;
  fill: #696969;
}
.dots-icon {
  width: 24px;
  color: #696969;
}
.card {
  width: 10rem;
}
.exit {
  width: 22px;
}
.end-pointer {
  height: 8px;
  width: 8px;
  border: 1px solid gray;
  background-color: white;
  border-radius: 9999999px;
  position: absolute;
  bottom: 0;
  right: -3px;
}
.plus {
  position: absolute;
  height: 14px;
  width: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgb(94, 94, 236);
  color: white;
  top: 30px;
  border-radius: 99999999px;
  right: -7px;
}
.plus-text {
  margin-bottom: 2px;
}
</style>
