<template>
    <div class="conmmon-rule">
        <div>
            普通名单：<button class="button" @click="addCommonRule">添加普通名单</button>
        </div>
        <div class="bodyList">
            普通默认配置邀请人数：<input type="number" name="commonDefaultNum" v-model="commonDefaultNum" />
            开始商品价格（单位：分）: <input type="number" v-model="startPrice" />
            结束商品价格（单位：分）: <input type="number" v-model="endPrice" />
            <input type="button" class="button" value="删除本条">
            <div>
                规则（1）：开始已售出数量：<input type="number" name="startNumber" />
                结束已售出数量：<input type="number" name="endNumber" />
                需要邀请人数量：<input type="number" name="inviterNumber" />
                <input type="button" value="删除">
            </div>
            <hr />
        </div>
</template>
