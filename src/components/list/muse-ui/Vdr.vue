<template>
<div>
<div class="normal">
      <vdr
        ref="vdr"
        :w="100"
        :h="100"
        :parent="true"
        :debug="false"
        :isConflictCheck="true"
        :snap="true"
        :snapTolerance="20"
        :disable-user-select="false"
        class-name-dragging="my-dragging-class"
        class-name="my-class1"
        @resizing="onResize"
        :z="99"
      >
        <slot></slot>
      </vdr>
  </div>

</div>

</template>

<script>
var elementResizeDetectorMaker = require("element-resize-detector");
import vdr from "vue-draggable-resizable-gorkys";
import "vue-draggable-resizable-gorkys/dist/VueDraggableResizable.css";
export default {
  components: { vdr },
  data() {
    return {
      width: 0,
      height: 0,
      x: 0,
      y: 0,
    };
  },

  computed: {
    moveChildAttribute() {
      return {
        width: this.$store.state.Attribute.moveChildren.width,
        height: this.$store.state.Attribute.moveChildren.height,
      };
    },
  },

  methods: {
    onResize: function (x, y, width, height) {
      this.x = x;
      this.y = y;
      this.width = width;
      this.height = height;
      // console.log(this.height)
    },
    onDrag: function (x, y) {
      this.x = x;
      this.y = y;
    },
  },
 
};
</script>

<style scoped>
.normal{
  position: relative;
}
.my-class1 {
  position: absolute;
  background: olive;
}
.my-class2 {
  position: absolute;
  background: orangered;
}
.my-class3 {
  position: absolute;
  background: palegreen;
}
.normal > div {
  position: absolute;
}
#drag-dom{
    width: 200px;
    height: 200px;
    background: purple;
}
</style>