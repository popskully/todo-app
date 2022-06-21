<template>
  <div class="container p-5 md:p-20 mx-auto">
    <div class="flex flex-col space-y-3">
      <h1 class="font-semibold text-4xl text-slate-900">Hi there,</h1>
      <p v-if="tasks.length < 2" class="text-slate-500 text-xl">
        You have {{ tasks.length }} task listed
      </p>
      <p v-else class="text-slate-500 text-xl">
        You have {{ tasks.length }} tasks listed
      </p>
      <!-- search -->
      <div class="flex rounded-lg space-x-5 pt-10 justify-center">
        <input
          type="text"
          v-model="task"
          placeholder="Create a new task..."
          class="px-3 py-1 md:py-3 text-lg md:text-2xl rounded-lg bg-transparent transition duration-300 ease-in-out focus:bg-white hover:bg-white focus:outline-none hover:border-blue-300 focus:border-blue-300 border-2 text-gray-600 w-3/4"
        />
        <button
          @click="submitTask"
          class="bg-blue-500 rounded-lg hover:opacity-80 transition hover:duration-300 ease-in-out text-white text-2xl p-2 md:py-3 md:px-3"
        >
          <svg
            viewBox="0 0 32 32"
            class="w-6 h-6 md:w-8 md:h-8"
            fill="currentColor"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g data-name="Layer 45" id="Layer_45">
              <path
                class="cls-1"
                d="M19.47,31a2,2,0,0,1-1.8-1.09l-4-7.57a1,1,0,0,1,1.77-.93l4,7.57L29,3.06,3,12.49l9.8,5.26,8.32-8.32a1,1,0,0,1,1.42,1.42l-8.85,8.84a1,1,0,0,1-1.17.18L2.09,14.33a2,2,0,0,1,.25-3.72L28.25,1.13a2,2,0,0,1,2.62,2.62L21.39,29.66A2,2,0,0,1,19.61,31Z"
              />
            </g>
          </svg>
        </button>
      </div>
      <div class="lg:px-28 py-10">
        <span
          v-if="tasks.length < 1"
          class="bg-white drop-shadow-sm flex flex-col w-full p-5 rounded-lg text-lg text-slate-900 font-medium"
          ><p class="text-center mx-auto">Sorry, you have no task listed</p>
          <img class="w-14 h-14 mx-auto" src="./icons/sad.gif" alt="" />
        </span>
        <table v-else class="table-auto w-full bg-white rounded-lg">
          <thead>
            <tr class="border-b-2 border-[#f6f6f6]">
              <th
                class="p-5 text-left text-slate-900 text-sm w-2/4 md:text-lg font-semibold"
              >
                Task
              </th>
              <th
                class="p-5 text-left text-slate-900 text-sm w-1/4 md:text-lg font-semibold"
              >
                Status
              </th>
              <th
                class="p-5 text-left text-slate-900 text-sm w-1/4 md:text-lg font-semibold"
              >
                Edit/Delete
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(task, index) in tasks" :key="index">
              <td
                class="p-5 text-left text-slate-900 w-3/4 text-md font-medium"
              >
                <span
                  :class="{
                    'line-through text-slate-500': task.status === 'Completed',
                    'no-underline text-slate-900': task.status === 'Pending',
                  }"
                >
                  {{ task.name }}
                </span>
              </td>
              <td
                class="p-5 text-left text-slate-900 w-3/4 text-md font-medium"
              >
                <span
                  @click="changeStatus(index)"
                  :class="{
                    'line-through text-slate-500': task.status === 'Completed',
                    'no-underline text-slate-900': task.status === 'Pending',
                  }"
                >
                  {{ task.status }}
                </span>
              </td>
              <td
                class="p-5 text-left text-slate-100 space-x-2 md:space-x-5 text-md flex font-medium"
              >
                <button
                  @click="editTask(index)"
                  class="rounded-lg p-2 bg-blue-500"
                >
                  <svg
                    class="w-5 h-5"
                    id="svg8"
                    version="1.1"
                    viewBox="0 0 185.20832 185.20832"
                  >
                    <defs id="defs2" />
                    <g id="layer1" transform="translate(244.17261,202.68451)">
                      <g id="g2151" transform="translate(106.90778,902.20758)">
                        <path
                          d="m -172.90538,-1050.9226 c 3.39877,-2.5377 2.99925,-7.8285 0,-10.8277 l -36.20385,-36.2043 c -2.99924,-2.9992 -7.82831,-2.9992 -10.82755,0 l -58.71681,58.6149 -58.63793,58.53587 c -3.02589,18.77157 -6.1309,37.62221 -9.15691,56.3938 l 56.18187,-9.36844 c 30.37245,-30.37282 44.72497,-44.67089 59.21122,-59.10268 14.48613,-14.43185 28.73348,-28.62465 58.14996,-58.04145 z"
                          id="path851"
                          style="
                            opacity: 1;
                            fill: none;
                            fill-opacity: 1;
                            fill-rule: nonzero;

                            stroke-width: 9.26041603;
                            stroke-linecap: round;
                            stroke-linejoin: round;
                            stroke-miterlimit: 6.19999981;
                            stroke-dasharray: none;
                            stroke-dashoffset: 0;
                            stroke-opacity: 1;
                            paint-order: normal;
                          "
                          stroke="currentColor"
                        />
                        <rect
                          height="67.306938"
                          id="rect919"
                          ry="5.0819001"
                          fill="currentColor"
                          style="
                            opacity: 1;

                            fill-opacity: 1;
                            fill-rule: nonzero;
                            stroke: none;
                            stroke-width: 9.26041603;
                            stroke-linecap: round;
                            stroke-linejoin: round;
                            stroke-miterlimit: 6.19999981;
                            stroke-dasharray: none;
                            stroke-dashoffset: 0;
                            stroke-opacity: 1;
                            paint-order: normal;
                          "
                          transform="matrix(-0.70710294,0.70711062,-0.70710294,-0.70711062,0,0)"
                          width="11.06725"
                          x="-601.16461"
                          y="865.35944"
                        />
                        <path
                          d="m -312.8744,-925.23385 -32.29813,-32.29847 -1.2759,33.12229 z"
                          id="path925"
                          fill="currentColor"
                          style="
                            stroke: none;
                            stroke-width: 0.26458332px;
                            stroke-linecap: butt;
                            stroke-linejoin: miter;
                            stroke-opacity: 1;
                          "
                        />
                        <rect
                          height="67.306938"
                          id="rect927"
                          ry="5.0819001"
                          fill="currentColor"
                          style="
                            opacity: 1;

                            fill-opacity: 1;
                            fill-rule: nonzero;
                            stroke: none;
                            stroke-width: 9.26041603;
                            stroke-linecap: round;
                            stroke-linejoin: round;
                            stroke-miterlimit: 6.19999981;
                            stroke-dasharray: none;
                            stroke-dashoffset: 0;
                            stroke-opacity: 1;
                            paint-order: normal;
                          "
                          transform="matrix(-0.70710294,0.70711062,-0.70710294,-0.70711062,0,0)"
                          width="11.06725"
                          x="-467.45428"
                          y="865.7829"
                        />
                      </g>
                    </g>
                  </svg>
                </button>
                <button
                  @click="deleteTask(index)"
                  class="rounded-lg p-2 bg-pink-500"
                >
                  <svg
                    viewBox="0 0 32 32"
                    class="w-5 h-5"
                    fill="currentColor"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <title />
                    <g data-name="Layer 17" id="Layer_17">
                      <path
                        class="cls-1"
                        d="M24,31H8a3,3,0,0,1-3-3V9A1,1,0,0,1,7,9V28a1,1,0,0,0,1,1H24a1,1,0,0,0,1-1V9a1,1,0,0,1,2,0V28A3,3,0,0,1,24,31Z"
                      />
                      <path
                        class="cls-1"
                        d="M28,7H4A1,1,0,0,1,4,5H28a1,1,0,0,1,0,2Z"
                      />
                      <path
                        class="cls-1"
                        d="M20,7a1,1,0,0,1-1-1V3H13V6a1,1,0,0,1-2,0V2a1,1,0,0,1,1-1h8a1,1,0,0,1,1,1V6A1,1,0,0,1,20,7Z"
                      />
                      <path
                        class="cls-1"
                        d="M16,26a1,1,0,0,1-1-1V11a1,1,0,0,1,2,0V25A1,1,0,0,1,16,26Z"
                      />
                      <path
                        class="cls-1"
                        d="M21,24a1,1,0,0,1-1-1V13a1,1,0,0,1,2,0V23A1,1,0,0,1,21,24Z"
                      />
                      <path
                        class="cls-1"
                        d="M11,24a1,1,0,0,1-1-1V13a1,1,0,0,1,2,0V23A1,1,0,0,1,11,24Z"
                      />
                    </g>
                  </svg>
                </button>
                <button
                  v-if="task.status === 'Pending'"
                  @click="changeStatus(index)"
                  class="rounded-lg p-2 transition duration-300 ease-in-out bg-green-500"
                >
                  <svg
                    viewBox="0 0 512 512"
                    class="w-5 h-5"
                    xmlns="http://www.w3.org/2000/svg"
                    fill="currentColor"
                  >
                    <path
                      d="M173.898 439.404l-166.4-166.4c-9.997-9.997-9.997-26.206 0-36.204l36.203-36.204c9.997-9.998 26.207-9.998 36.204 0L192 312.69 432.095 72.596c9.997-9.997 26.207-9.997 36.204 0l36.203 36.204c9.997 9.997 9.997 26.206 0 36.204l-294.4 294.401c-9.998 9.997-26.207 9.997-36.204-.001z"
                    />
                  </svg>
                </button>
                <button
                  v-else
                  @click="changeStatus(index)"
                  class="rounded-lg p-2 transition duration-300 ease-in-out bg-gray-500"
                >
                  <svg
                    class="w-5 h-5"
                    fill="currentColor"
                    id="Layer_1"
                    style="enable-background: new 0 0 32 32"
                    version="1.1"
                    viewBox="0 0 32 32"
                    xml:space="preserve"
                    xmlns="http://www.w3.org/2000/svg"
                    xmlns:xlink="http://www.w3.org/1999/xlink"
                  >
                    <path
                      d="M28,16c-1.219,0-1.797,0.859-2,1.766C25.269,21.03,22.167,26,16,26c-5.523,0-10-4.478-10-10S10.477,6,16,6  c2.24,0,4.295,0.753,5.96,2H20c-1.104,0-2,0.896-2,2s0.896,2,2,2h6c1.104,0,2-0.896,2-2V4c0-1.104-0.896-2-2-2s-2,0.896-2,2v0.518  C21.733,2.932,18.977,2,16,2C8.268,2,2,8.268,2,16s6.268,14,14,14c9.979,0,14-9.5,14-11.875C30,16.672,28.938,16,28,16z"
                    />
                  </svg>
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",

      editedTask: null,
      statuses: ["Pending", "Completed"],
      tasks: [],
    };
  },
  mounted() {
    // if(task === ""){
    // }
  },
  methods: {
    capitalizeFirstChar(str) {
      return str.charAt(0).toUppercase() + str.slice(1);
    },
    changeStatus(index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status);
      if (++newIndex > 1) newIndex = 0;
      this.tasks[index].status = this.statuses[newIndex];
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    submitTask() {
      if (this.task.length === 0) return;
      if (this.editedTask != null) {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      } else {
        this.tasks.push({
          name: this.task,
          status: "Pending",
        });
      }
      this.task = "";
    },
  },
};
</script>

<style></style>
