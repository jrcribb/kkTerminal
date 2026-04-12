<template>
  <el-icon :style="statusStyle" >
    <CircleCloseFilled v-if="statusType === -2" />
    <WarningFilled v-else-if="statusType === -1" />
    <SuccessFilled v-else-if="statusType === 1" />
    <InfoFilled v-else />
  </el-icon>
</template>

<script>
import { computed } from "vue";
import {
  SuccessFilled,
  WarningFilled,
  CircleCloseFilled,
  InfoFilled,
} from "@element-plus/icons-vue";

export default {
  name: 'CmdCodeStatus',
  components: {
    SuccessFilled,
    WarningFilled,
    CircleCloseFilled,
    InfoFilled,
  },
  props: {
    status: {
      type: String,
      default: 'success',
    },
    style: {
      type: Object,
      default: (() => {}),
    },
  },
  setup(props) {

    const statusTypeDict = {
      'Compile Error': -2,
      'Execute Interrupt': -1,
      'Not Active': 0,
      'Execute Success': 1,
    };

    const statusColor = ['#f56c6c','#e6a23c','#909399','#67c23a'];

    const statusType = computed(() => {
      return statusTypeDict[props.status] || 0;
    });

    const statusStyle = computed(() => {
      return {
        fontSize: '16px',
        ...props.style,
        color: statusColor[statusType.value + 2],
      }
    });

    return {
      statusType,
      statusStyle,
    }
  }
}
</script>

<style>
</style>
