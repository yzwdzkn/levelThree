<template>
<div>
    一级区域：<select v-model= "one"  v-on:change="changeLevelOne">
    <option v-for= 'one in levelOneAll' :value= "one.id" >{{one.name}}</option>
    </select>
    二级区域：<select v-model= "two" v-on:change="changeLevelTwo">
    <option v-for= "two in levelTwoAll" :value= "two.id">{{two.name}}</option>
    </select>
    三级区域：<select v-model= "three" v-on:change="changeLevelThree">
    <option v-for= "three in levelThreeAll" :value= "three.id">{{three.name}}</option>
    </select>
</div>

</template>

<script>
export default {
    props:['levelOneAll','id1','id2','id3'],
  data () {
    return {
      one: '',
      two: '',
      three: '',
      levelTwoAll: [],
      levelThreeAll:[],
    }
  },
  methods:{
      //改变一级菜单
    changeLevelOne(){
    //   console.log('一级菜单:',this.one);
      this.$emit('onLevelOne',this.one);//发送请求给父组件的事件 方法名为 'onLevelOne'  参数为 this.one
    },
    //获取二级菜单
    getLevelTwo(levelTwoAll){
    //   console.log('二级菜单:',levelTwoAll);
      this.levelTwoAll = levelTwoAll;
    },
    //改变二级菜单
    changeLevelTwo(){
    //   console.log('子组件二级菜单的id：',this.two);
      this.$emit('onLevelTwo',this.two);//发送请求给父组件的事件 方法名为 'onLevelTwo'  参数为 this.two
    },
    //获取三级菜单
    getLevelThree(levelThreeAll){
    // console.log('三级菜单',levelThreeAll);
      this.levelThreeAll = levelThreeAll;
    },
    //改变三级菜单
    changeLevelThree(){
    //   console.log('子组件三级菜单的id：',this.three);
      this.$emit('onLevelThree',this.three);//发送请求给父组件的事件 方法名为 'onLevelThree'  参数为 this.three
    }
  },
  mounted: async function(){
    var self = this;
    for(var i in this.levelOneAll){
        if(self.id1 == this.levelOneAll[i].id){
            this.one = self.id1;
            this.changeLevelOne();
            for(var j in this.levelTwoAll){
                if(self.id2 == this.levelTwoAll[j].id){
                    this.two = self.id2;
                    this.changeLevelTwo();
                    for(var l in this.levelThreeAll){
                        if(self.id3 == this.levelThreeAll[l].id){
                            this.three = self.id3
                            this.changeLevelThree();
                            return;
                        }
                    }
                }
            }
        }else{
            this.one = this.levelOneAll[0].id;
            this.changeLevelOne();
            this.two = this.levelTwoAll[0].id;
            this.changeLevelTwo();
            this.three = this.levelThreeAll[0].id;
            this.changeLevelThree();
        }
    }
   }
}
</script>