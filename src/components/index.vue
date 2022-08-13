<template>
    <div>
        <listTop @costum='change'/>

        <listDown :list='arr'  @colation='handle'/>
    </div>



</template>

<script>
  import listTop from './listTop.vue'
  import listDown from './listDown.vue'
  export default{
    components:{
      listTop,
      listDown
    },
    data(){
      return{
        arr: [
            {
                topId: 0,
                imgSrc: '../../刻晴2.jpg',
                productName: "背带裤",
                productPrice: 10,
                productNum: 1,
                pickFlag: false,

            },
            {
                topId: 1,
                imgSrc: '../../刻晴2.jpg',
                productName: "背带裤",
                productPrice: 20,
                productNum: 1,
                pickFlag: false,
            },
            {
                topId: 2,
                imgSrc: '../../刻晴2.jpg',
                productName: "背带裤",
                productPrice: 30,
                productNum: 1,
                pickFlag: false,
            }
        ],
        flag: '',
        flag2: '',
      }
    },
    methods:{
        change(input){
            console.log(input);
            this.arr.push(input)
        },
        handle(id){
            this.arr = this.arr.filter(item=>item.topId!=id)   
        }   

    }
  } 


</script>

<style>
 .top {
        width: 500px;
        /* height:80px; */
        border: 1px solid;
        padding: 10px;
    }

    th,
    td {
        height: 50px;
    }

    .bottom {
        border: 1px solid;
        width: 520px;
        border-collapse: collapse;
        border-spacing: 0px;

    }

    .bottom thead th {
        border: 1px solid black;
        background-color: deepskyblue;
        color: white;
    }

    .bottom tbody td {
        border: 1px solid;
        text-align: center;
    }

    img {
        width: 30px;
        /* height: 10px; */
    }

    #app {
        width: 600px;
        height: 400px;
        margin: 100px auto;
    }
</style>