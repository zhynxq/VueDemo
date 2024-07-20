<!-- eslint-disable vue/require-v-for-key -->
<template>
    <div class="menu">
        <div class="header">
            <input v-model="toname" type="text" name="" id="" placeholder="请输入添加的内容">
            <button @click="add">添加</button> 
        </div>
        <section v-for="(itme,index) in list" :key="itme.id">
            <ul>
                <li>
                    <div class="view">
                        <span>{{index + 1}}</span><label for="">{{itme.name}}</label>
                        <button @click="del(itme.id)">×</button>
                    </div>
                </li>
            </ul>
        </section>
    </div>
  
</template>

<script>
export default {
    data(){
        return{
            list:[
                {id:1,name:'跑步'},
                {id:2,name:'走路'},
                {id:3,name:'散步'},
            ],
            toname:''
        }
    },
    methods:{
        del(id){
            this.list = this.list.filter(itme=>itme.id !== id)
        },
        add(){
            if(this.toname){
               this.list.unshift({
                id: +new Date(),
                name:this.toname
            })
            this.toname = '' 
            localStorage.setItem('list',JSON.stringify(this.list))
            this.getList() 
            }else{
                alert("请输入内容：")
            }
           
        },
        getList(){
            this.list = JSON.parse(localStorage.getItem('list'))
            console.log(this.list);
        }
    }
}
</script>

<style>
    .menu{
        margin: 0 auto;
        border:2px solid rgb(193, 124, 34) ;
        width: 800px;
        height: 100%;
        /* background-color: rgb(167, 27, 50); */
    } 
    li{
        list-style: none;
    }
    header{
        display: inline-block;
        width: 700px;
        /* height: 30px; */
        /* border: 1px solid #e0b7b6; */
    }
    input{
        border: 0;
        /* border-right: 0; */
        display: inline-block;
        width: 89%;
        height: 30px;
    }
    button{
        display: block;
        border: 1px solid #e0b7b6;
        float: right;
        width: 10%;
        height: 30px;
        color: white;
        background-color: #e0b7b6;
    } 
    .view{
        width: 100%;
        height: 30px;
        border-top:2px solid rgb(193, 124, 34);
    }
    span{
        display: inline-block;
        font-size: 16px;
    }
    label{
        display: inline-block;
        margin-left: 20px;
        font-size: 16px;
    }

</style>