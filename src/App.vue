<template>
  <div>
    <form-item-render
      :dynamic-form-data="dynamicFormData"
      :form-item-list="formList"
      @update:dynamic-form-data="onDynamicFormDataUpdate"
    >
    </form-item-render>
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
      formList,
      dynamicFormData: {
        startDate: '2000-02-02',
        endDate: '3000-02-02',
        productName: 'test product',
        iisWoman: true,
        accAmt: 1000000
      }
    }
  },
  methods: {
    onDynamicFormDataUpdate(data) {
      // debugger
      console.log(this.dynamicFormData, 'value')
      this.dynamicFormData = data
    }
  }
}
</script>
