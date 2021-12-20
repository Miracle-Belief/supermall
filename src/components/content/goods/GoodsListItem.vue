<template>
  <div class="goos-item" @click="itemClick">
      <img :src="goodsItem.show.img" alt="" @load="imgLoad">
      <div class="goods-info">
        <p>{{goodsItem.title}}</p>
        <span class="price">{{goodsItem.price}}</span>
        <span class="collect">{{goodsItem.cfav}}</span>
      </div>
  </div>
</template>

<script>
  export default {
    name: 'GoodsListItem',
    props: {
      goodsItem: {
        type: Object,
        default() {
          return []
        }
      }
    },
    methods: {
      imgLoad() {
        this.$bus.$emit('itemImageLoad')
      },
       itemClick() {
        this.$router.push('/detail/' + this.goodsItem.iid)
      },
    }
  }
</script>

<style scoped>
.goos-item {
  width: 48%;
  padding-bottom: 40px;
  position: relative;
}
.goos-item img {
  width: 100%;
  border-radius: 5px;
}
.goods-info {
  font-size: 12px;
  position: absolute;
  bottom: 5px;
  left: 0;
  right: 0;
  overflow: hidden;
  text-align: center;
}
.goods-info p {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin-bottom: 3px;
}
.goods-info .price {
  color: var(--color-height-text);
  margin-right: 20px;
}
.goods-info .collect {
  position: relative;
}
.goods-info .collect::before {
  content: '';
  position: absolute;
  left: -15px;
  top: -1px;
  width: 14px;
  height: 14px;
  background: url("~assets/img/common/uncollect.svg");
  background-size: 100%;
  background-repeat: no-repeat;
  background-position: center;
}
</style>
