<template>
    <table class="bottom">
        <thead>
            <th>

                全选<input type="checkbox" >
                反选<input type="checkbox" >

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
                    <input type="checkbox" >
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
        props:['list']
        ,
        methods:{
            del(id){
                this.$emit('colation',id)
            }
        },
        computed:{
            total(){
                return 
            }
        }

    }


</script>