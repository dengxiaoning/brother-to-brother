<template>
    <div class="nav-top">
        <div class="go-back" >
            <i class="el-icon-arrow-left icon-back"></i>
        </div>
        <div class="map-name" >{{name}}</div>
        <div class="icon-style">
            <i class="el-icon-edit icon-size"  @click="showEditDialog"></i>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
    import BToB from './b_to_b.js';

    export default {
        name: "header_component",
        data(){
          return{
              name:'春节联欢晚会'
          }
        },
        created(){
            this.listenBtoBFromEdit();
        },
        methods:{
            showEditDialog(){
                BToB.$emit("switch_dialog",true);
            },
            listenBtoBFromEdit(){
                BToB.$on("update_template_params",val =>{
                    this.name = val;
                })
            },

        }
    }
</script>

<style scoped  lang="less" >
    .nav-top {
        position: fixed;
        top: 0;
        left: 0;
        height: 40px;
        line-height: 40px;
        width: 100%;
        background: rgba(28, 30, 46, 1);
        border-bottom: 1px solid #fff;
        box-sizing: border-box;
        z-index: 99;
    }
    .go-back {
        position: absolute;
        left: 0;
        top: 0;
        z-index: 11;
        text-align: center;
        line-height: 39px;
        width: 40px;
        height: 40px;
        background: linear-gradient(
                17deg,
                rgba(56, 77, 218, 1) 0%,
                rgba(40, 132, 209, 1) 100%
        );
        box-shadow: 0px 4px 10px 0px rgba(188, 205, 232, 0.1);
    }
    .map-name {
        float: left;
        color: #fff;
        font-size: 14px;
        margin-left: 57px;
    }
    .map-name-text {
        float: left;
        color: #000;
        background: #fff;
        height: 24px;
        line-height: 24px;
        width: 142px;
        margin-left: 57px;
        border: 0;
        outline: none;
        margin-top: 8px;
        font-size: 12px;
        box-sizing: border-box;
        padding: 0 5px;
    }
    .icon-style {
        float: left;
        color: #676976;
        font-size: 18px;
        margin-left: 12px;
        vertical-align: middle;
    i:hover {
        color: #2e74d4;
    }
    }
    .icon-size {
        font-size: 16px;
        cursor: pointer;
        color: #ffffff;
    }
    .icon-back {
        font-size: 20px;
        color: #fff;
    }
    .icon-left {
        margin-left: 10px;
    }
</style>