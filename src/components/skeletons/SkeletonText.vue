<template>
  <div>
    <div class="flex">
      <div
        class="relative w-5/6 skeleton skeleton-text skeleton-loader__bone"
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
</template>

<script>
export default {
  name: "SkeletonText"
};
</script>

<style scoped></style>
