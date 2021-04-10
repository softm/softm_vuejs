<template>
    <div :style="{backgroundColor:bgColor}">
        <h1>{{mainTitle}} to {{title}}</h1>
        <input type="text" v-model="input1"/>
        <button type="button" @click="getValue">get</button>
        <button type="button" @click="setValue">set</button>
        <select class="form-control" v-model="region" @change="changeRegion"> 
            <option :key="i" :value="d.v" v-for="(d,i) in regions" >{{d.t}}</option>
        </select>
        <table class="table table-borderd" v-show="tableShow">
        <!-- <table class="table table-borderd" v-if="tableShow"> -->
            <tr :key="i" v-for="(d, i) in regions">
            <td>{{d.v}}</td>
            <td>{{d.t}}</td>
            </tr>
        </table>
    </div>
</template>
<script>
export default {
    data() {
        return {
            bgColor:'yellowGreen',
            mainTitle : "Welcome",
            title : "개발자의 품격",
            input1: "입력값.",
            regions:[
                {v:"S",t:"Seoul"}
              , {v:"J",t:"Jeju"}
              , {v:"B",t:"Busan"}
            ],
            region:"S",
            tableShow : true,
        }
    },
    watch: {
        input1() {
            console.log(this.input1);
            //alert("변경됨");
        },
        region() {
            console.log(this.region);
            //alert("변경됨");
        }
    },
    methods: {
        getValue() {
            alert( this.input1 );
        },
        setValue() {
            this.input1  = "1234";
        },
        changeRegion() {
            alert(this.region);
        }
    },
    beforeCreate() {
        // console.log("beforeCreate");
    },
    created() {
        // console.log("created");
    },
    beforeMount() {
        // console.log("beforeMount");
    },
    mounted() {
        // console.log("mounted");
    },
    beforeUpdate() {
        // console.log("beforeUpdate");
    },
    updated() {
        // console.log("updated");
    },
    beforeDestroy() {
        // console.log("beforeDestroy");
    },
    destroyed() {
        // console.log("destroyed");
    },
    name:"Home"
};
</script>
