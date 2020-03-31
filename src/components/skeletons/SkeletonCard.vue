<template>
  <div class="max-w-sm rounded overflow-hidden shadow-lg">
    <div
      class="relative skeleton skeleton-image w-full skeleton-loader__bone"
    ></div>
    <div class="px-6 py-4">
      <div class="mt-3 skeleton skeleton-title font-bold text-xl mb-2"></div>
      <div class="flex">
        <div
          class="relative mt-6 w-5/6 skeleton skeleton-text skeleton-loader__bone"
        ></div>
      </div>
      <div class="flex">
        <div
          class="relative mt-2 w-3/6 skeleton skeleton-text skeleton-loader__bone"
        ></div>
      </div>
      <div class="flex">
        <div
          class="relative mt-2 w-4/6 skeleton skeleton-text skeleton-loader__bone"
        ></div>
      </div>
    </div>
    <div class="mt-2 px-6 py-4">
      <div
        class="relative ml-auto skeleton skeleton-button skeleton-loader__bone"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SkeletonCard"
};
</script>

<style scoped></style>
