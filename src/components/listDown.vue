<template>
    <table class="bottom">
        <thead>
            <th>

                全选<input type="checkbox" v-model="flag" @click='allPick'>
                反选<input type="checkbox" @click='rePick'>

            </th>
            <th>产品图片</th>
            <th>编号</th>
            <th>品牌名称</th>
            <th>价格</th>
            <th>数量</th>
            <th>操作</th>
        </thead>
        <tbody>
            <tr v-for='item in list' :key='item.id'>
                <td>
                    <input type="checkbox" v-model='item.pickFlag'>
                </td>
                <td>
                    <img :ssc='item.imgSrc'>
                </td>
                <td>{{item.topId}}</td>
                <td>{{item.productName}}</td>
                <td>{{item.productPrice}}</td>
                <td>
                    <button>+</button>
                    {{item.productNum}}
                    <button >-</button>
                </td>
                <td>
                    <button @click='del(item.topId)'>删除</button>
                </td>
            </tr>
            <tr class="total">
                <td>总计</td>
                <td colspan="6">
                   {{total}}
                </td>
            </tr>
        </tbody>
    </table>



</template>


<script>
    export default{
        props:['list','turn']
        ,
        data(){
            return{
                flag:this.turn
            }
        },
        methods:{
            del(id){
                this.$emit('colation',id)
            },
            allPick(){
                console.log(this.flag);
                this.list.forEach(item => {
                    item.pickFlag =  !this.flag
                });
            },
            rePick(){
                this.list.forEach(item => {
                    item.pickFlag = !item.pickFlag 
                });
            }
        },
        computed:{
            total(){
                let totalPrice = 0
                let arr2 = this.list.filter(item=>item.pickFlag)
                return (arr2.reduce((totalPrice,item)=>{
                       return totalPrice += (item.productPrice*item.productNum)
                },0))
               
            }
        }

    }


</script>