<template>
  <va-sidebar
    :width="width"
    :minimized="minimized"
    :minimizedWidth="minimizedWidth"
  >
    <h1 class="display-1 heading-font">Score</h1>
    <filp-number :value="counter" :speed="600" :digitCount="2" />
    <va-button @click="inc">Click Me</va-button>
  </va-sidebar>
</template>

<script>
import { useGlobalConfig } from "vuestic-ui";
import FilpNumber from "@/components/FlipNumber";

export default {
  name: "room-sidebar",
  components: {
    FilpNumber
  },
  props: {
    width: { type: String, default: "16rem" },
    color: { type: String, default: "secondary" },
    minimized: { type: Boolean, required: true },
    minimizedWidth: {
      type: Boolean,
      required: false,
      default: undefined
    }
  },
  data() {
    return {
      counter: 0
    };
  },
  computed: {
    computedClass() {
      return {
        "app-sidebar--minimized": this.minimized
      };
    },
    colors() {
      return useGlobalConfig().getGlobalConfig().colors;
    }
  },
  methods: {
    inc() {
      this.counter++;
      // if (this.counter <= 8) this.counter++;
      // else {
      //   this.counter = 0;
      // }
    }
  }
};
</script>

<style lang="scss">
.va-sidebar {
  .va-collapse__body {
    margin-top: 0 !important;
  }

  &__menu {
    padding: 2rem 0;
    &__inner {
      padding-bottom: 8rem;
    }
  }

  &-item {
    &-content {
      padding: 0.75rem 1rem;
    }

    &__icon {
      width: 1.5rem;
      height: 1.5rem;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
}
</style>

<style lang="scss" scoped>
.va-sidebar {
  flex-shrink: 0;
}

// .va-sidebar--minimized {
//   width: auto !important;
// }
</style>
