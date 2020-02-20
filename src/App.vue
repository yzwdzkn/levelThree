<template>
<div>
    <v-regioncomponet ref='levelTwoAll' v-bind:levelOneAll= 'levelOneAll' :id1= 'id1' :id2= 'id2' :id3= 'id3' @onLevelOne='onLevelOne' @onLevelTwo='onLevelTwo' @onLevelThree='onLevelThree'></v-regioncomponet>
</div>
</template>
<script>
import Regioncomponet from './components/regioncomponet.vue'
export default {
    data () {
        return{
            levelOneAll:[//省
                {id:1,name:'浙江省'},
                {id:2,name:'江苏省'},
                {id:3,name:'广东省'},
            ],
            levelTwoAll:[//市
                {id:1,name:'杭州市',parentId:1},
                {id:2,name:'温州市',parentId:1},
                {id:3,name:'绍兴市',parentId:1},
                {id:4,name:'苏州市',parentId:2},
                {id:5,name:'无锡市',parentId:2},
                {id:6,name:'南京市',parentId:2},
                {id:7,name:'广州市',parentId:3},
                {id:8,name:'江门市',parentId:3},
                {id:9,name:'汕头市',parentId:3},
            ],
            levelThreeAll:[//区
                {id:1,name:'萧山区',parentId:1},
                {id:2,name:'余杭区',parentId:1},
                {id:3,name:'龙湾区',parentId:2},
                {id:4,name:'鹿城区',parentId:2},
                {id:5,name:'越城区',parentId:3},
                {id:6,name:'柯桥区',parentId:3},
                {id:7,name:'吴中区',parentId:4},
                {id:8,name:'姑苏区',parentId:4},
                {id:9,name:'惠山区',parentId:5},
                {id:10,name:'滨湖区',parentId:5},
                {id:11,name:'玄武区',parentId:6},
                {id:12,name:'鼓楼区',parentId:6},
                {id:13,name:'越秀区',parentId:7},
                {id:14,name:'白云区',parentId:7},
                {id:15,name:'江海区',parentId:8},
                {id:16,name:'新会区',parentId:8},
                {id:17,name:'龙湖区',parentId:9},
                {id:18,name:'金平区',parentId:9},
            ],
            id1:2,
            id2:4,
            id3:7,
            }
    },
    components:{
        'v-regioncomponet':Regioncomponet,
    },
    methods:{
        onLevelOne(id){
            // console.log('父组件拿到省份id:',id)
            var levelTwo = [];
                this.levelTwoAll.forEach(function(item,index) {
                    if(item.parentId==id){
                        levelTwo.push(item)
                        }
                });
                        this.$refs.levelTwoAll.getLevelTwo(levelTwo)
            },
        onLevelTwo(id){
            // console.log('父组件拿到城市id:',id)
            var levelThree = [];
                this.levelThreeAll.forEach(function(item,index) {
                    if(item.parentId==id){
                        levelThree.push(item)
                        }
                });
                    this.$refs.levelTwoAll.getLevelThree(levelThree)
            },
        onLevelThree(id){
            // console.log('父组件拿到区县id:',id)
            }
    }
    
}
</script>
