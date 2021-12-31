<template>
  <div
    class="skeleton"
    :class="{ rounded, customClass }"
    :style="[
      `width:${width}px;height:${height}px;`,
      borderRadius,
      `--animation-duration: ${animationDuration}s;`,
    ]"
  ></div>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";

export default defineComponent({
  name: "Skeleton",
  props: {
    width: {
      type: Number,
      required: true,
    },
    height: {
      type: Number,
      required: true,
    },
    radius: {
      type: Number,
      default: 0,
    },
    rounded: {
      type: Boolean,
      default: false,
    },
    animationDuration: {
      type: Number,
      default: 1,
    },
    customClass: {
        type: String,
        default: ''
    }
  },

  setup({ rounded, radius }) {
    const borderRadius = computed(() =>
      rounded ? "" : `border-radius: ${radius}px;`
    );
    return { borderRadius };
  },
});
</script>

<style lang="scss">
.skeleton {
  position: relative;
  overflow: hidden;
  background-color: #dddbdd;

  &::after {
    content: "";
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    transform: translateX(-100%);
    background-image: linear-gradient(
      90deg,
      rgba(#fff, 0) 0,
      rgba(#fff, 0.2) 20%,
      rgba(#fff, 0.5) 60%,
      rgba(#fff, 0)
    );
    animation: shimmer infinite;
    animation-duration: var(--animation-duration);
  }

  @keyframes shimmer {
    100% {
      transform: translateX(100%);
    }
  }
}
.rounded {
  border-radius: 50%;
}
</style>
