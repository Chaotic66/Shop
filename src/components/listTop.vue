<template>
<div class="top">
        编号：<input type="text" v-model="topId">
        品牌名称：<input type="text" v-model="productName">
        价格：<input type="text" v-model="productPrice">
        <button @click='add'>提交</button>

        
    </div>
</template>

<script>
    
    export default{
        data(){
            return{
                topId:'',
                productName:'',
                productPrice:'',
                pickFlag:false,
                imgSrc: '../../刻晴2.jpg',
            }
        },
        methods:{
            add(){
                this.$emit('costum',{
                    topId: this.topId,
                    productName: this.productName,
                    productPrice: this.productPrice,
                    pickFlag: this.pickFlag,
                    imgSrc: this.imgSrc,
                    productNum:1
                })
                this.topId='',
                this.productName='',
                this.productPrice=''

            }
        }

    }


</script>