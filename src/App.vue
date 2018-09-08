<template>
  <div id="app">
    <baidu-map class="bm-view" id="bm-div" center="柳州市广西科技大学" :zoom="15" :scroll-wheel-zoom="true">
        <bm-copyright style="display: block"
                anchor="BMAP_ANCHOR_TOP_RIGHT"
                :copyright="[{id: 1, content: '<a href=\'http://tieba.baidu.com/f?kw=%B9%E3%CE%F7%BF%C6%BC%BC%B4%F3%D1%A7&fr=ala0&tpl=5\'><img src=\'./tieba2.png\' height=\'46px\'></a>'}]">
        </bm-copyright>
        <bm-map-type :map-types="['BMAP_NORMAL_MAP', 'BMAP_HYBRID_MAP']" anchor="BMAP_ANCHOR_TOP_LEFT"></bm-map-type>
        <bm-geolocation anchor="BMAP_ANCHOR_BOTTOM_RIGHT" :showAddressBar="true" :autoLocation="true"></bm-geolocation>

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
  #bm-div > div > div.BMap_cpyCtrl.BMap_noprint.anchorTR > span{
      display: block !important;
  }
</style>
