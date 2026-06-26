<template>
<div>
  <form-item-render></form-item-render>
</div>
</template>

<script>
import formItemRender from "./components/formItemRender.vue"
export default {
  name: "App",
  components: {
   formItemRender,
  }
}
</script>