<template>
  <div
    v-bind:class="flipped ? 'flip-container flipped' : 'flip-container'"
    :style="`height: ${height}px; width: ${width}px;`"
  >
    <div class="flipper">
      <div class="slot-container front" v-on:click="toggleFront">
        <slot name="front"></slot>
      </div>
      <div class="slot-container back" v-on:click="toggleBack">
        <slot name="back"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FlipCard",
  props: {
    height: {
      type: Number,
      default: 160
    },
    width: {
      type: Number,
      default: 120
    },
    enabled: {
      type: Boolean,
      default: true
    }
  },
  emits: ["flip"],
  data: function() {
    return {
      flipped: false
    };
  },
  methods: {
    toggleFront() {
      if (this.enabled) {
        this.flipped = true;
        this.$emit("flip", true);
      } else {
        this.$emit("flip", -1);
      }
    },
    toggleBack() {
      if (this.enabled) {
        this.flipped = false;
        this.$emit("flip", false);
      } else {
        this.$emit("flip", -1);
      }
    }
  }
};
</script>

<style type="text/css" scoped>
i.frontFlipBtn,
i.backFlipBtn {
  position: absolute;
  right: 20px;
  top: 20px;
  color: #ffffff;
}
i.backFlipBtn {
  -webkit-transform: rotateY(-180deg);
  -moz-transform: rotateY(-180deg);
  -o-transform: rotateY(-180deg);
  -ms-transform: rotateY(-180deg);
  transform: rotateY(-180deg);
}
.flip-container {
  -webkit-perspective: 1000;
  -moz-perspective: 1000;
  -o-perspective: 1000;
  perspective: 1000;
}
.flipper {
  -moz-transform: perspective(1000px);
  -moz-transform-style: preserve-3d;
  position: relative;
  display: flex;
  height: 100%;
}
.slot-container {
  display: flex;
  height: 100%;
  background: #ffffff;
  justify-content: center;
  align-items: center;
  border-radius: 5px;
  border: 1px solid #e5e5e5;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}
.front,
.back {
  -webkit-backface-visibility: hidden;
  -moz-backface-visibility: hidden;
  -o-backface-visibility: hidden;
  backface-visibility: hidden;
  -webkit-transition: 0.6s;
  -webkit-transform-style: preserve-3d;
  -moz-transition: 0.6s;
  -moz-transform-style: preserve-3d;
  -o-transition: 0.6s;
  -o-transform-style: preserve-3d;
  -ms-transition: 0.6s;
  -ms-transform-style: preserve-3d;
  transition: 0.6s;
  transform-style: preserve-3d;
  top: 0;
  left: 0;
  width: 100%;
}
.back {
  -webkit-transform: rotateY(-180deg);
  -moz-transform: rotateY(-180deg);
  -o-transform: rotateY(-180deg);
  -ms-transform: rotateY(-180deg);
  transform: rotateY(-180deg);
  position: absolute;
}
.flip-container.flipped .back {
  -webkit-transform: rotateY(0deg);
  -moz-transform: rotateY(0deg);
  -o-transform: rotateY(0deg);
  -ms-transform: rotateY(0deg);
  transform: rotateY(0deg);
}
.flip-container.flipped .front {
  -webkit-transform: rotateY(180deg);
  -moz-transform: rotateY(180deg);
  -o-transform: rotateY(180deg);
  -ms-transform: rotateY(180deg);
  transform: rotateY(180deg);
}
.front {
  z-index: 2;
}
</style>
