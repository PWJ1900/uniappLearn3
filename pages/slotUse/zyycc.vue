<template>
 <div class="child">
    <h3>这里是子组件</h3>
    <slot name="demo" :text="account" :record="user"></slot>
  </div>
</template>

<script>
export default {
    name:"child",
    data(){
      return {
        user: ['张三','李四',"王五"],
        account:"ray"
      }
    }
}
</script>