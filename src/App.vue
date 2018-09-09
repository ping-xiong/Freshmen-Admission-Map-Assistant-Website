<template>
  <div id="app">
    <baidu-map class="bm-view" id="bm-div" center="柳州市广西科技大学" :zoom="15" :scroll-wheel-zoom="true">
        <bm-copyright style="display: block"
                anchor="BMAP_ANCHOR_TOP_LEFT"
                :copyright="[{id: 1, content: '<a href=\'http://tieba.baidu.com/f?kw=%B9%E3%CE%F7%BF%C6%BC%BC%B4%F3%D1%A7&fr=ala0&tpl=5\'><img src=\'./tieba2.png\' height=\'46px\'></a>'}]">
        </bm-copyright>
        <bm-geolocation anchor="BMAP_ANCHOR_TOP_RIGHT" :showAddressBar="true" :autoLocation="true" :offset="locPostion"></bm-geolocation>
        <bm-transit v-if="isNav" :start="start" :end="end" :auto-viewport="true" location="柳州市"></bm-transit>
    </baidu-map>
    <toolbar v-on:changNavBychild="changNavBychild"></toolbar>
      <div id="bottom"></div>
  </div>
</template>

<script>
import 'iview/dist/styles/iview.css';
import Toolbar from './components/toolbar'


export default {
  name: 'app',
    components: {Toolbar},
    data(){
      return{
          clientHeight: 0,
          locPostion:{
              width:10,
              height:10
          },
          start:"",
          end:"",
          isNav:false
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
        changNavBychild(start, end){
            this.start = start;
            this.end = end;
            if (this.start == ""){
                this.isNav = false;
            } else{
                this.isNav = true;
            }
        }
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
  #bm-div > div > div.BMap_cpyCtrl.BMap_noprint.anchorTL > span{
      display: block !important;
  }
</style>
