<template>
  <el-dialog v-model="dialogVisible" title="设置" width="80%" draggable :modal="false" :close-on-click-modal="false" modal-class="wqdy-custom-dialog">
    <el-container style="height: 100%" class="container">
      <el-tabs tab-position="left">
        <!-- <el-tab-pane label="winex"> -->
        <!-- <el-tabs> -->
        <el-tab-pane label="信息">
          <Info />
        </el-tab-pane>
        <!-- <el-tab-pane label="console">
            <Console />
          </el-tab-pane> -->
        <el-tab-pane label="医保卡">
          <Suspense>
            <Card identityTypeCode="152691"></Card>
          </Suspense>
        </el-tab-pane>
        <el-tab-pane label="身份证">
          <Suspense>
            <Card identityTypeCode="152695"></Card>
          </Suspense>
        </el-tab-pane>
        <el-tab-pane label="永居证">
          <Suspense>
            <Card identityTypeCode="399668724"></Card>
          </Suspense>
        </el-tab-pane>
        <el-tab-pane label="存储storage">
          <Suspense>
            <StorageCopy></StorageCopy>
          </Suspense>
        </el-tab-pane>
      </el-tabs>
    </el-container>
  </el-dialog>
</template>

<script setup lang="ts">
import { ref, onMounted, computed, reactive } from 'vue'
import Console from './console.vue'
import Info from './info.vue'
import Card from './card.vue'
import WinSearchHistory from './WinSearchHistory.vue'
import StorageCopy from './StorageCopy.vue'

const props = defineProps({
  modelValue: Boolean
})
const emit = defineEmits(['update:modelValue'])

const dialogVisible = computed({
  get() {
    return props.modelValue
  },
  set(val) {
    emit('update:modelValue', val)
  }
})
console.log(dialogVisible)
</script>

<style scoped lang="scss"></style>
<style lang="scss">
.wqdy-custom-dialog {
  pointer-events: none;
  .wqdy-overlay-dialog {
    pointer-events: none;
  }
  .wqdy-dialog {
    pointer-events: auto;
  }
}
</style>
