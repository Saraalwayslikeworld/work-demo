<template>
    <div class="commonRule">
        <div class="box">
            <label>普通默认配置邀请人数：</label>
            <input type="number" v-model="commonRuleItem.defaultInviterNumber" />
        </div>
        <div class="box">
            <label>开始商品价格（单位：分）: </label>
            <input type="number" v-model="commonRuleItem.startPrice" />
            <label>结束商品价格（单位：分）: </label>
            <input type="number" v-model="commonRuleItem.endPrice" />
        </div>
        <div v-for="(item,idx) in commonRuleItem.ruleList" :key="idx">
            <div class="box">
                <div> 规则 - {{idx+1}}</div>
                <label>开始已售出数量</label><input type="number" v-model="item.startNumber" />
                <label> 结束已售出数量：</label><input type="number" v-model="item.endNumber" />
                <label>需要邀请人数量：</label><input type="number" v-model="item.inviterNumber" />
                <button class="button" @click="delItem(idx)">删除本条规则</button>
                <hr />
            </div>
        </div>
        <div class="box">
            <button class="button" @click="addItem">新增规则</button>
        </div>
    </div>
</template>
<script>
export default {
  props: {
    commonRuleItem: {
      type: Object,
      default: {
        commonDefaultNum: 0,
        pItemId: 0,
        ruleList: [
          {
            startNumber: 0,
            endNumber: 0,
            inviterNumber: 0,
          },
        ],
      },
    },
    index: {
      type: Number,
    },
  },
  data() {
    return {
      //   commonRuleItems: this.commonRuleItem,
    };
  },
  methods: {
    addItem() {
      let item = {
        startNumber: 0,
        endNumber: 0,
        inviterNumber: 0,
      };
      this.commonRuleItem.ruleList.push(item);
    },
    delItem(idx) {
      this.commonRuleItem.ruleList.splice(idx, 1);
    },
    save() {},
  },
};
</script>

<style>
.commonRule {
  border: 1px solid #333;
  background: rgba(0, 0, 0, 0.1);
}
.box {
  margin: 20px 10px;
}
</style>
