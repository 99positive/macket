<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
      <slot  name="item-icon"></slot>
    </div>
    <div v-else >
      <slot name="item-icon-active"></slot>
    </div>
    <div :class="{active: isActive}" :style="activeStyle">
      <slot :class="{active: isActive}" name="item-text"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TabBarItem',
  props: {
    path: String,
    activeClolor: {
      type: String,
      default: "red",
    }
  },
  data() {
    return {

    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) != -1
    },
    activeStyle() {
      return this.isActive ? {color: this.activeClolor} : {}
    }
  },
  methods: {
    itemClick() {
      this.$router.replace(this.path)
    }
  }
}
</script>


<style scoped>
  .tab-bar-item {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
    color:black;
  }
  .tab-bar-item img {
    width: 24px;
    height: 24px;
    vertical-align: middle;
    margin: 4px 0 2px 0;
  }
  .actived {
    color:coral;
    font-weight: bolder;
  }
</style>
