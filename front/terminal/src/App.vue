<template>
  <FrameWork></FrameWork>
</template>

<script>
import FrameWork from "./views/FrameWork";

export default {
  name: 'App',
  components: {
    FrameWork,
  }
}
</script>

<style>
/* 禁止图片拖拽 */
img {
  -webkit-user-drag: none; /* Safari */
  -khtml-user-drag: none; /* Konqueror HTML */
  -moz-user-drag: none; /* Firefox */
  -o-user-drag: none; /* Opera */
}

.kk-dialog-class {
  pointer-events: none;
  z-index: 3456;
}

.el-dialog {
  pointer-events: auto;
}

.el-popconfirm__main {
  user-select: none;
  margin-top: 2px;
}

/* 文本不可选中 */
.no-select {
  user-select: none;
}

</style>