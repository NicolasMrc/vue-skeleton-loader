<template>
  <div id="app" class="p-12">
    <div class="pb-4 flex border-b">
      <div class="w-1/2 pt-8 pr-4 text-right">
        <span class="text-gray-800 text-xl">Vue Skeleton Loader</span>
      </div>
      <div class="w-1/2">
        <div class="flex">
          <div class="md:w-1/3 px-3 mb-6 md:mb-0">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="grid-state"
            >
              Type
            </label>
            <div class="relative">
              <select
                v-model="type"
                @change="fakeLoading"
                class="block appearance-none w-full bg-gray-200 border border-gray-200 text-gray-700 py-3 px-4 pr-8 rounded leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
                id="grid-state"
              >
                <option
                  v-for="type in types"
                  :key="`select_type_${type.value}`"
                  :value="type.value"
                  >{{ type.label }}</option
                >
              </select>
              <div
                class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700"
              >
                <svg
                  class="fill-current h-4 w-4"
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 20 20"
                >
                  <path
                    d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"
                  />
                </svg>
              </div>
            </div>
          </div>
          <div class="w-1/3 pt-8">
            <button
              type="button"
              class="px-3 py-1 bg-blue-500 text-white rounded"
              @click="fakeLoading"
            >
              Replay
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="flex mt-12">
      <div class="pl-12 pb-6 w-1/2">
        <div>
          <span class="text-xl">
            Résultat
          </span>
        </div>
        <skeleton-loader :loading="loading" :type="type" class="mt-12">
          <fake-card v-if="type === 'card'"></fake-card>
          <fake-button v-else-if="type === 'button'"></fake-button>
          <fake-title v-else-if="type === 'title'"></fake-title>
          <fake-text v-else-if="type === 'text'"></fake-text>
        </skeleton-loader>
      </div>
    </div>
  </div>
</template>

<script>
import SkeletonLoader from "./components/skeletons/SkeletonLoader.vue";
import FakeCard from "./components/fakers/fakeCard";
import FakeButton from "./components/fakers/fakeButton";
import FakeTitle from "./components/fakers/fakeTitle";
import FakeText from "./components/fakers/fakeText";

export default {
  name: "App",
  components: {
    FakeText,
    FakeTitle,
    FakeButton,
    FakeCard,
    SkeletonLoader
  },
  data: () => ({
    loading: true,
    types: [
      { label: "Card", value: "card" },
      { label: "Title", value: "title" },
      { label: "Text", value: "text" },
      { label: "Button", value: "button" }
    ],
    type: "card"
  }),
  created() {
    this.fakeLoading();
  },
  methods: {
    fakeLoading() {
      this.loading = true;
      const self = this;
      setTimeout(function() {
        self.loading = false;
      }, 2000);
    }
  }
};
</script>

<style lang="scss">
@tailwind base;
@tailwind components;
@tailwind utilities;

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
