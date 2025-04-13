<template>
  <div class="item-grid">
    <slot name="header"></slot>
    <div class="grid-container">
      <slot
        name="item"
        v-for="(item, index) in items"
        :item="item"
        :index="index"
        :key="index"
      ></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style>
.item-grid {
  margin-bottom: 30px;
}

.grid-container {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
}

.artist-card {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 0 10px;
}

.artist-img {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 5px;
}

.artist-name {
  font-size: 14px;
  text-align: center;
}

.chart-item {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.chart-rank {
  font-weight: bold;
  margin-right: 10px;
  width: 20px;
}

.chart-name {
  flex: 1;
}
</style>