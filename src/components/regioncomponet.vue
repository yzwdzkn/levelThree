<template>
<div>
    <select v-model= "prov" v-on:change="changeProv">
    <option disabled value="0">请选择省份/地区:</option>
    <option v-for= 'province in provinceAll' :value= "province.id" >{{province.name}}</option>
    </select>
    <select v-model= "city" v-on:change="changeCity">
    <option disabled value="0">请选择城市</option>
    <option v-for= "city in cityAll" :value= "city.id">{{city.name}}</option>
    </select>
   <select v-model= "area" v-on:change="changeArea">
    <option disabled value="0">请选择区县</option>
    <option v-for= "area in areaAll" :value= "area.id">{{area.name}}</option>
    </select>
</div>

</template>

<script>
export default {
    props:['provinceAll'],
  data () {
    return {
      prov: '',
      city: '',
      area: '',
      cityAll: [],
      areaAll:[],
    }
  },
  methods:{
    changeProv(){//改变省会
      console.log('子组件的id:',this.prov)
      this.$emit('updateProv',this.prov)//发送请求给父组件的事件 方法名为 'updateProv'  参数为 this.prov
    },
    getCity(city){//获取城市
      console.log('子组件的city:',city)
      this.cityAll = city;
    },
    changeCity(){//改变城市
      console.log('子组件城市的id：',this.city)
      this.$emit('updateCity',this.city)//发送请求给父组件的事件 方法名为 'updateCity'  参数为 this.city
    },
    getArea(area){//获取区县
    console.log(area)
      this.areaAll = area;
    },
    changeArea(){//改变区县
      console.log('子组件区县的id：',this.area)
      this.$emit('updateArea',this.area)//发送请求给父组件的事件 方法名为 'updateArea'  参数为 this.area
    }
  }
}
</script>