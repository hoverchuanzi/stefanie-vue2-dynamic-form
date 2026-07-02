<template>
  <div>
    <form-item-render
      :dynamic-form-data="dynamicFormData"
      :form-item-list="formList"
      @update:dynamic-form-data="onDynamicFormDataUpdate"
    >
    </form-item-render>
    <a-button type="primary" @click="submitForm">提交</a-button>
    <p>{{ text }}</p>
  </div>
</template>

<script>
import formItemRender from './components/formItemRender.vue'
import formList from './api/index.json'

export default {
  name: 'App',
  components: {
    formItemRender
  },
  data() {
    return {
      text: '',
      formList,
      dynamicFormData: {
        startDate: '2000-02-02',
        endDate: '2200-02-02',
        productName: 'test product',
        iisWoman: true,
        accAmt: 1000000
      }
    }
  },
  methods: {
    onDynamicFormDataUpdate(data) {
      // debugger
      this.dynamicFormData = data
      console.log(this.dynamicFormData, 'value')
    },
    submitForm() {
      this.text = JSON.stringify(this.dynamicFormData)
    }
  }
}
</script>
