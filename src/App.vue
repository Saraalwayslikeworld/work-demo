<template>
  <div id="app">
    <div class="box">
      <textarea cols="200" rows="5" v-model="resultText"></textarea>
      <p><button class="button" @click="parseResult">解析配置</button></p>
      <p><button @click="createResult">生成结果</button></p>
    </div>
    <div class="box">
      默认配置邀请人数：<input type="number" v-model="result.defaultInviterNumber" />
    </div>
    <div class="specialItemRuleList box">
      <label>特殊名单：</label>
      <button class="button" @click="addSpecialRule">添加特殊名单</button>
      <div v-for="(item,rIdx) in result.specialItemRuleList" :key="rIdx">
        <div class="box">
          <button class="button" @click="delSpecialRuleItem(rIdx)">删除本条</button>
          <special-rule :special-rule-item="item" :index="rIdx"></special-rule>
        </div>
      </div>
    </div>
    <div class="commonItemRuleList box">
      <label>普通名单：</label>
      <button class="button" @click="addCommonRule">添加普通名单</button>
      <div v-for="(item,rIdx) in result.commonItemRuleList" :key="rIdx">
        <div class="box">
          <button class="button" @click="delCommonRuleItem(rIdx)">删除本条</button>
          <common-rule :common-rule-item="item" :index="rIdx"></common-rule>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import commonRule from './components/commonRule.vue';
import specialRule from './components/specialRule.vue';
export default {
  name: 'app',
  components: {
    specialRule,
    commonRule,
  },
  data() {
    return {
      result: {
        defaultInviterNumber: 0,
        specialItemRuleList: [],
        commonItemRuleList: [],
      },
      resultText: '',
    };
  },
  methods: {
    addSpecialRule() {
      let item = {
        defaultInviterNumber: 0,
        pItemId: 0,
        ruleList: [
          {
            startNumber: 0,
            endNumber: 0,
            inviterNumber: 0,
          },
        ],
      };
      this.result.specialItemRuleList.push(item);
    },
    delSpecialRuleItem(idx) {
      this.result.specialItemRuleList.splice(idx, 1);
    },
    addCommonRule() {
      let item = {
        startPrice: 0,
        defaultInviterNumber: 0,
        ruleList: [
          {
            startNumber: 0,
            endNumber: 0,
            inviterNumber: 0,
          },
        ],
        endPrice: 0,
      };
      this.result.commonItemRuleList.push(item);
    },
    delCommonRuleItem(idx) {
      this.result.commonItemRuleList.splice(idx, 1);
    },
    createResult() {
      this.resultText = JSON.stringify(this.result);
    },
    parseResult() {
      this.result = JSON.parse(this.resultText);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
.box {
  /* margin: 30px; */
}
</style>
