<template>
  <div class='form-wrapper'>
    <a-form :form="form" layout="inline" size="small">
      <template v-for="(formItem, index) in formItemList">
        <template v-if="formItem.type === 'input'">
          <a-form-item :key="index" :label="formItem.label">
            <a-input placeholder="Basic usage" :disabled="formItem.disabled" />
          </a-form-item>
        </template>
        <template v-if="formItem.type === 'number'">
          <a-form-item :key="index" :label="formItem.label">
            <a-input-number :disabled="formItem.disabled"  />
          </a-form-item>
        </template>
        <template v-if="formItem.type === 'date'">
          <a-form-item :key="index" :label="formItem.label">
            <a-date-picker :disabled="formItem.disabled"/>
          </a-form-item>
        </template>
        <template v-if="formItem.type === 'checkbox'">
          <a-form-item :key="index" :label="formItem.label">
            <a-checkbox :disabled="formItem.disabled">
            </a-checkbox>
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
    }
  }

}
</script>

<style>
.form-wrapper {
  padding: 20px 450px;
}
</style>