<template>
  <div id="app">
    <baidu-map class="bm-view" id="bm-div" :center="{lng: 116.404, lat: 39.915}" :zoom="15" :scroll-wheel-zoom="true">
    </baidu-map>
  </div>
</template>

<script>

export default {
  name: 'app',
    data(){
      return{
          clientHeight: 0
      }
    },
    mounted(){
      this.clientHeight =  `${document.documentElement.clientHeight}`;
        window.onresize = function temp() {
            this.clientHeight = `${document.documentElement.clientHeight}`;
        };
    },
    watch:{
        clientHeight: function () {
            this.changeFixed(this.clientHeight)
        }
    },
    methods: {
        changeFixed(clientHeight) {                        //动态修改样式
            document.getElementById("bm-div").style.height = clientHeight + 'px';
        },
    }
}
</script>

<style>
  .bm-view{
    width: 100%;
  }
    body{
        margin: 0;
        padding: 0;
    }
</style>
