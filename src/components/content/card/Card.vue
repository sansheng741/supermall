<template>
  <div class="card">
    <card-item v-for="(item,index) in cardData"
               :goods="item"
               :key="index"/>
  </div>
</template>

<script>
import CardItem from "@/components/content/card/CardItem";

export default {
  name: "Card",
  components: {CardItem},
  props: {
    cardData: {
      type: Array,
      default() {
        return []
      }
    }
  }
}
</script>

<style scoped>
.card {
  display: flex;
  flex-wrap: wrap;
}
</style>
