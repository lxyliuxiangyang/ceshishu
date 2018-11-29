<template>
    <div>
      <home-header ></home-header>
      <home-swiper :swiper="swiperlist"></home-swiper>
      <icons :iconlist="iconslist"></icons>
      <remcoment :remcoment="remcomentlist"></remcoment>
      <weekd :week="weekdlist"></weekd>
    </div>
</template>

<script>
  import  HomeHeader  from './components/homeheader'
  import  HomeSwiper  from './components/swiper'
  import  Icons from './components/icons'
  import  Remcoment from './components/remcoment'
  import Weekd from './components/weekd'
  import axios from 'axios'
    export default {
      name: "home",
      components:{
          HomeHeader,
          HomeSwiper,
          Icons,
          Remcoment,
          Weekd
      },
      data(){
        return{

          swiperlist:[],
          iconslist:[],
          remcomentlist:[],
          weekdlist:[],
          // 类型只是表示没有实际意义
        }
      },
      mounted (){
      this.githomelist()
      },
      methods:{
        githomelist(){
        axios.get("/api/index.json").then((res)=>{
            res=res.data
              if(res.status=="0"){

                  this.swiperlist=res.data.swiperlist,
                  this.iconslist=res.data.iconlist
                  this.remcomentlist=res.data.remcomentList
                this.weekdlist=res.data.weekendList
                console.log(this.weekdlist)
              }

        })
        }
      }
    }
</script>

<style scoped>

</style>
