<template>
<div>
  <form-item-render :form-item-list="formList"></form-item-render>
</div>
</template>

<script>
import formItemRender from "./components/formItemRender.vue"
export default {
  name: "App",
  components: {
   formItemRender,
  },
  data() {
    return {
     formList: [
       {
         field: "startDate",
         label: "开始时间",
         type: "date",
         required: true,
         visible: true,
         disabled: false,
         defaultValue: "",
         placeholder: "",
         span: 12
       },
       {
         field: "startDate",
         label: "结束时间",
         type: "date",
         required: true,
         visible: true,
         disabled: true,
         defaultValue: "",
         placeholder: "",
         span: 12
       },
       {
         field: "productName",
         label: "产品名称",
         type: "input",
         required: true,
         visible: true,
         disabled: true,
         defaultValue: "",
         placeholder: "",
         span: 12
       },
       {
         field: "iisWoman",
         label: "过滤",
         type: "checkbox",
         required: true,
         visible: true,
         disabled: false,
         defaultValue: "",
         placeholder: "",
         span: 12
       },
       {
         field: "accAmt",
         label: "收款",
         type: "number",
         required: true,
         visible: true,
         disabled: false,
         defaultValue: "",
         placeholder: "",
         span: 12
       },


     ]
    }
  }
}
</script>