<template>
  <div class="form-wrapper">
    <a-form :form="dynamicFormData" layout="inline" size="small">
      <template v-for="(formItem, index) in formItemList">
        <template v-if="formItem.type === 'input'">
          <a-form-item :key="index" :label="formItem.label">
            <a-input
              placeholder="Basic usage"
              :disabled="formItem.disabled"
              v-model="localFormData[formItem.field]"
            />
          </a-form-item>
        </template>
        <template v-else-if="formItem.type === 'number'">
          <a-form-item :key="index" :label="formItem.label">
            <a-input-number :disabled="formItem.disabled" v-model="localFormData[formItem.field]" />
          </a-form-item>
        </template>
        <template v-else-if="formItem.type === 'date'">
          <a-form-item :key="index" :label="formItem.label">
            <a-date-picker :disabled="formItem.disabled" v-model="localFormData[formItem.field]" />
          </a-form-item>
        </template>
        <template v-else-if="formItem.type === 'checkbox'">
          <a-form-item :key="index" :label="formItem.label">
            <a-checkbox :disabled="formItem.disabled" v-model="localFormData[formItem.field]" />
          </a-form-item>
        </template>
        <template v-else-if="formItem.type === 'rate'">
          <a-form-item :key="index" :label="formItem.label">
            <a-rate v-model="localFormData[formItem.field]" :disabled="formItem.disabled" />
          </a-form-item>
        </template>
      </template>
    </a-form>
  </div>
</template>
<script>
export default {
  props: {
    formItemList: {
      type: Array,
      default() {
        return []
      }
    },
    dynamicFormData: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  data() {
    return {
      localFormData: { ...this.dynamicFormData }, // 本地表单数据(其实是一个副本)
      syncing: false
    }
  },
  watch: {
    dynamicFormData: {
      handler(newVal) {
        this.localFormData = { ...newVal }
      },
      deep: true
    },
    localFormData: {
      handler() {
        if (this.syncing) return
        this.syncing = true
        this.$emit('update:dynamic-form-data', { ...this.localFormData })
        this.$nextTick(() => {
          this.syncing = false
        })
      },
      deep: true
    }
  }
}
</script>

<style>
.form-wrapper {
  padding: 20px 450px;
}
</style>
