<template>
<div>
  <ul>
    <li @click="goDetail" v-for="item in musicList" :key="item.id">
      <img :src="item.bg" alt="">
    </li>
  </ul>
</div>
</template>
<script>
  import store from '@/vuex/store'
  import axios from 'axios'

  export default({
    data(){
        return{
          musicList:[]
        }
    },
    store,
    created(){
      this.$store.commit('routerLink',{
        color:'rgb(0,150,136)',
        title:'音乐'
      })
      this.getDate();
    },
    methods:{
        getDate(){
            axios.get('./static/data/musiclist.json').then((res)=>{
                this.musicList=res.data.albums
            }).catch(()=>{

            })
      },
      goDetail(){
        this.$router.push('/musicdetail')
      }
    }

  })
</script>
<style scoped>
  ul{
    display: flex;
    flex-wrap: wrap;
  }
  ul li {
    width: 50%;
    /*float: left;*/
    /*display: inline-block;*/
  }
  ul li img{
    width: 100%;
  }
</style>
