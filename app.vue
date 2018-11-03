<template>
    <div id="app">
        <div>
            默认配置邀请人数：<input type="number" v-model="defaultInviterNumber" />
        </div>
        <div class="specialItemRuleList">
            <div>
                特殊名单：<button class="button" @click="addCommonRule">添加特殊名单</button>
            </div>
            <div class="box">

            </div>
        </div>
    </div>
</template>
<script>
export default {
  data() {
    return {
      defaultInviterNumber: 0,
    };
  },
};
</script>
<style>
.box {
  margin: 30px;
}
</style>

