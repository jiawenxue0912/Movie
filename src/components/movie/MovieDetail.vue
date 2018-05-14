<template>
  <div>
    <div class="detail-top">
      <div class="dt-left">
        <img :src="detailData.img">
      </div>
      <div class="dt-right">
        {{detailData.nm}}
      </div>
      <div class="dt-right">
        {{detailData.sc}}
      </div>
      <div class="dt-right">
        {{detailData.cat}}
      </div>
      <div class="dt-right">
        {{detailData.src}}{{detailData.dur}}
      </div>
    </div>
    <div class="detail-center">
      {{detailData.dir}}
    </div><br>
    <div class="detail-bottom">
      {{detailData.dra}}
    </div>
  </div>
</template>
<script>
  import axios from 'axios'
  export default({
    created(){
      this.getData()
    },
    methods:{
      getData(){
        axios.get(API_PROXY+'http://m.maoyan.com/movie/'+this.detailId+'.json').then((res)=>{
          console.log(res.data.data.MovieDetailModel);
          this.detailData=res.data.data.MovieDetailModel
        }).catch((res)=>{
          console.log('error')
        })
      }
    },
    data(){
      return {
        detailId:this.$route.params.movieId,
        detailData:{
        }
      }
    }
  })
</script>
<style scoped>
.dt-left{
  float: left
}
  .dt-right {
    font-size: 20px;
  }
  .detail-bottom{
    font-size: 17px;
  }
</style>
