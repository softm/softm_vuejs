<template>
 <div>
   <h1>This is Home Page</h1>
   <SoftmFE :title="title">
     <template v-slot:header="{slotData}">
     <!-- is same -->
     <!-- <template #header> -->
        <h1>Hello Slot Header - {{slotData}}</h1>
     </template>
     <template #default>
        <h1>Default Slot</h1>
     </template>
   </SoftmFE>
   <form action="">
     <InputField :name="name" @update-name="updateName"/>
     <InputFieldVmodel v-model="name"/>
     <button>submit</button>
   </form>
   {{name}}
 </div>
</template>

<script>
import SoftmFE from '@/components/SoftmFE.vue';
import InputField from '@/components/InputField.vue';
import InputFieldVmodel from '@/components/InputFieldVmodel.vue';

export default {
  name: 'Home',
  components:{
    SoftmFE,
    InputField,
    InputFieldVmodel,
  },
  data() {
    return {
      title: "Home Title",
      name:"test11"
    }
  },
  methods:{
    updateName(name) {
      this.name = name;
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