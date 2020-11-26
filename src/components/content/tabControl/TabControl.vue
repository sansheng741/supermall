<template>
  <div class="tab-control">
    <div v-for="(item,index) in title"
         :key="index"
         class="table-control-item"
         :class="{active: index === currentIndex}"
         @click="itemClick(index)">
      <span>{{ item }}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  data() {
    return {
      currentIndex: 1
    }
  },
  props: {
    title: {
      type: Array,
      default() {
        return []
      }
    }
  },
  methods: {
    itemClick(index) {
      this.currentIndex = index;
    }
  }
}
</script>

<style scoped>
.tab-control {
  display: flex;
  text-align: center;
  line-height: 44px;
  height: 44px;
  font-size: 15px;

  position: sticky;
  top: 44px;
  background-color: #fff;
}

.table-control-item {
  flex: 1;

}

.table-control-item span {
  padding: 5px;
}

.active span{
  color: var(--color-high-text);
  border-bottom: 2px solid var(--color-tint);
}
</style>
