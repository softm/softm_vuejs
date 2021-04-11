<template>
  <div>
    <h1>{{title}}</h1>
    <p>{{name}}</p>
    <slot name="header" :slotData="slotData"></slot>
    <button @click="updateName">Change Name</button>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'SoftmFE',
  props:{
    title : {
      type: String,
      required: false,
      default: "default Title"
    }
  },
  data() {
    return {
      name : "Softm FE",
      slotData:"slot~data"
    }
  },
  methods:{
    updateName:function() {
      this.name = "Softm FE Updated";
    }
  }
}
</script>

<style scoped>
p {
  color :red;
}
</style>
