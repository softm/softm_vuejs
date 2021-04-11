<template>
  <div class="about">
    <h1>This is an about page</h1>
    <SoftmFE :title="title"></SoftmFE>
  </div>
</template>

<script>
import SoftmFE from '@/components/SoftmFE.vue';
export default {
  name: 'About',
  components:{
    SoftmFE
  },
  data() {
    return {
      title:"About page"
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
  color:red;
}
</style>