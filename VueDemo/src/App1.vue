<template>
  <div>
    <div v-if="!reportUrl">loading...</div>
    <div v-else> most start app is <a :href="reportUrl">{{reportName}}}</a></div>
  </div>
</template>

<script>
  import axios from 'axios'
  export default {
      data(){
          return{
              reportUrl:'',
              reportName:''
          }
      },
      mounted () {
        var url ='https://api.github.com/search/users?q=vue&sort=start';
        /*this.$http.get(url).then(
            response=>{
                const result = response.data;
                const item = result.items[0];
                this.reportUrl =item.html_url;
                this.reportName=item.login;
            },
            response=>{
              alert('请求失败');
            }
        )*/
       axios.get(url).then(response=>{
               const result = response.data
               const item = result.items[0];
               this.reportUrl =item.html_url;
               this.reportName=item.login;
           }).catch(error=>{
            alert('请求失败');
           })
      }
  }

</script>

<style>

</style>
