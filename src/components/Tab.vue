<!-- Tab -->
<template>
  <div class="Tab">
    <div
      :class="['item', { active: activeCode == item.code }]"
      v-for="item in tabList"
      :key="item.code"
      @click="tabChange(item.code)"
    >
      {{ item.name }} {{ item.num }}
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Tab",
  props: { tabList: { type: Array } },
  setup(props, { emit }) {
    console.log(" ~ props", props.tabList);
    const activeCode = ref(1);
    const tabChange = code => {
      activeCode.value = code;
    };
    return { activeCode, tabChange };
  }
};
</script>
<style lang="scss" scoped>
.Tab {
  display: flex;
  align-items: center;
  justify-content: space-around;
  height: 0.42rem;
  .item {
    font-size: 0.15rem;
    color: #6e727a;
    font-weight: bold;
  }
  .active {
    color: #ffffff;
    position: relative;
    &::after {
      content: "";
      height: 0.03rem;
      width: 40%;
      background: #ffffff;
      position: absolute;
      bottom: -0.11rem;
      left: 50%;
      transform: translate(-50%, 0);
      border-radius: 2px;
    }
  }
}
</style>
