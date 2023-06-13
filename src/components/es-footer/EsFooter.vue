<template>
  <div class="footer-container">
    <div class="custom-control custom-checkbox">
      <input type="checkbox" class="custom-control-input" id="fullCheck" :checked="isfull" @change="onCheckBoxChange" />
      <label class="custom-control-label" for="fullCheck">全选</label>
    </div>
    <!-- 合计区域 -->
    <div>
      <span>合计</span>
      <span class="amount">￥{{ amount.toFixed(2) }}</span>
    </div>
    <button type="button" class="btn btn-primary btn-settle" :disabled="total === 0">结算({{ total }})</button>
  </div>
</template>

<script>
export default {
  name: 'EsFooter',
  props: {
    amount: {
      type: Number,
      default: 0
    },
    total: {
      type: Number,
      default: 0
    },
    isfull: {
      type: Boolean,
      default: false
    }
  },
  emits: ['fullChange'],
  methods: {
    onCheckBoxChange(e) {
      console.log(e.target.checked)
      this.$emit('fullChange', e.target.checked)
    }
  }
}
</script>

<style lang="less" scoped>
.footer-container {
  height: 50px;
  width: 100%;
  background-color: #fff;
  border-top: 1px solid #efefef;
  position: fixed;
  bottom: 0;
  left: 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
}
.amount {
  font-weight: bold;
  color: red;
}
.btn-settle {
  min-width: 90px;
  height: 38px;
  border-radius: 19px;
}
</style>
