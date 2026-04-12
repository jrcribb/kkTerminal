<template>
  <div class="decoration-wrapper" >
    <CircleCloseFilled v-if="statusType === -1" :style="statusStyle" />
    <SuccessFilled v-else-if="statusType === 1" :style="statusStyle" />
    <Remove v-else :style="statusStyle" />
  </div>
</template>

<script>
import { computed } from "vue";
import {
  SuccessFilled,
  CircleCloseFilled,
  Remove,
} from "@element-plus/icons-vue";

export default {
  name: 'ShellStatus',
  components: {
    SuccessFilled,
    CircleCloseFilled,
    Remove,
  },
  props: {
    data: {
      type: Object,
      default: (() => {}),
    },
  },
  setup(props) {

    const statusColor = ['#f53f3f','#73767a','#00b42a'];

    const statusType = computed(() => {
      if(props.data.exitCode === 0) return 1;
      else if(!props.data.exitCode) return 0;
      else return -1;
    });

    const statusStyle = computed(() => {
      return {
        color: statusColor[statusType.value + 1],
        padding: '2px 2px',
        cursor: statusType.value !== 0 ? 'pointer' : '',
      }
    });

    return {
      statusType,
      statusStyle,
    }
  }
}
</script>

<style scoped>
.decoration-wrapper {
  position: relative;
}
</style>

<style>
.xterm-decoration-container .xterm-decoration {
  width: 16px !important;
  left: -16px !important;
}
</style>
