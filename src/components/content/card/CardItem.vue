<template>
  <div class="card-item">
    <div class="card-img">
      <a :href="goods.link"><img :src="goods.show.img" alt=""/></a>
    </div>
    <div class="details">
      <div class="title"><span>{{ goods.title }}</span></div>
      <div class="price"><span>{{ goods.price }}</span></div>
      <div class="popular-start"><span class="favorites">{{ goods.cfav }}</span></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardItem",
  props: {
    goods: {
      type: Object,
      default() {
        return {}
      }
    }
  }
}
</script>

<style scoped>
.card-item {
  position: relative;
  padding: 5px 3px 2px;
  width: 50%;
}

.card-img img {
  width: 100%;
}

.title span{
  display: block;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  margin-bottom: 3px;
}
.price{
  display: inline-block;
}
.popular-start{
  display: inline-block;
}
</style>
