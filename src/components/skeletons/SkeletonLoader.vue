<template>
  <div>
    <div v-if="loading">
      <component :is="selectedType"></component>
    </div>
    <div v-show="!loading">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import SkeletonCard from "./SkeletonCard";
import SkeletonTitle from "./SkeletonTitle";
import SkeletonButton from "./SkeletonButton";
import SkeletonText from "./SkeletonText";
export default {
  name: "SkeletonLoader",
  components: { SkeletonText, SkeletonButton, SkeletonTitle, SkeletonCard },
  props: {
    type: {
      type: String,
      default: "card"
    },
    loading: {
      type: Boolean,
      default: true
    }
  },
  computed: {
    selectedType() {
      switch (this.type) {
        case "card":
          return SkeletonCard;
        case "title":
          return SkeletonTitle;
        case "button":
          return SkeletonButton;
        case "text":
          return SkeletonText;
        default:
          return SkeletonCard;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
@-webkit-keyframes loading {
  100% {
    transform: translateX(100%);
  }
}

@keyframes loading {
  100% {
    transform: translateX(100%);
  }
}
.skeleton-loader__bone::after {
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.3),
    transparent
  );
  -webkit-animation: loading 1.5s infinite;
  animation: loading 1.5s infinite;
  content: "";
  height: 100%;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
  transform: translateX(-100%);
  z-index: 1;
}

.skeleton {
  background-color: #eee;

  &.skeleton-image {
    height: 200px;
  }
  &.skeleton-title {
    width: 200px;
    border-radius: 20px;
    height: 20px;
  }
  &.skeleton-text {
    border-radius: 20px;
    height: 13px;
  }
  &.skeleton-button {
    border-radius: 3px;
    height: 30px;
    width: 80px;
  }
}
</style>
