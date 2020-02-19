<template>
<div>
    <v-regioncomponet ref='cityAll' v-bind:provinceAll= 'provinceAll' @updateProv='updateProv' @updateCity='updateCity'></v-regioncomponet>
</div>
</template>
<script>
import Regioncomponet from './components/regioncomponet.vue'
export default {
    data () {
        return{
            provinceAll:[//省
                {id:1,name:'浙江省'},
                {id:2,name:'江苏省'},
                {id:3,name:'广东省'},
            ],
            cityAll:[//市
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
            areaAll:[//区
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
            }
    },
    components:{
        'v-regioncomponet':Regioncomponet,
    },
    methods:{
        updateProv(id){
            console.log('父组件拿到省份id:',id)
            var city = [];
                this.cityAll.forEach(function(item,index) {
                    if(item.parentId==id){
                        city.push(item)
                        }
                });
                        this.$refs.cityAll.getCity(city)
            },
        updateCity(id){
            console.log('父组件拿到城市id:',id)
            var area = [];
                this.areaAll.forEach(function(item,index) {
                    if(item.parentId==id){
                        area.push(item)
                        }
                });
                    this.$refs.cityAll.getArea(area)
            },
        updateArea(id){
            console.log('父组件拿到区县id:',id)
            }
    }
    
}
</script>
