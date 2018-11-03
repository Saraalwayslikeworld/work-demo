<template>
    <div class="specialRule">
        <div class="box">
            <label>特殊默认配置邀请人数：</label>
            <input type="number" v-model="specialRuleItem.defaultInviterNumber" />
        </div>
        <div class="box">
            <label>特殊商品pItemId:</label>
            <input type="number" v-model="specialRuleItem.pItemId" />
        </div>
        <div v-for="(item,idx) in specialRuleItem.ruleList" :key="idx">
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
    specialRuleItem: {
      type: Object,
      default: {
        specialDefaultNum: 0,
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
      //   specialRuleItems: this.specialRuleItem,
    };
  },
  methods: {
    addItem() {
      let item = {
        startNumber: 0,
        endNumber: 0,
        inviterNumber: 0,
      };
      this.specialRuleItem.ruleList.push(item);
    },
    delItem(idx) {
      this.specialRuleItem.ruleList.splice(idx, 1);
    },
    save() {},
  },
};
</script>

<style>
.specialRule {
  border: 1px solid #333;
  background: rgba(0, 0, 0, 0.1);
}
.box {
  margin: 20px 10px;
}
</style>

