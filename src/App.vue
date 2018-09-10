<template>
  <div id="app">
    <baidu-map class="bm-view" id="bm-div" :center="centerPoint" :zoom="zoom" :scroll-wheel-zoom="true" @click="get_point">
        <bm-copyright style="display: block"
                anchor="BMAP_ANCHOR_TOP_LEFT"
                :copyright="[{id: 1, content: '<a href=\'http://tieba.baidu.com/f?kw=%B9%E3%CE%F7%BF%C6%BC%BC%B4%F3%D1%A7&fr=ala0&tpl=5\'><img src=\'./tieba2.png\' height=\'46px\'></a>'}]">
        </bm-copyright>
        <bm-geolocation anchor="BMAP_ANCHOR_TOP_RIGHT" :showAddressBar="true" :autoLocation="true" :offset="locPostion"></bm-geolocation>
        <bm-transit v-if="isNav" :start="start" :end="end" :auto-viewport="true" location="柳州市"></bm-transit>
        <bm-tile
                :isTransparentPng="true"
                tileUrlTemplate="https://pingx.tech/app/maptiles/{Z}/tile-{X}_{Y}.png"
                v-if="isWaPian"
        >
        </bm-tile>
        <bm-marker :position="showPonit" animation="BMAP_ANIMATION_BOUNCE" v-if="isShowPoint">
            <bm-label :content="showPonitName" :labelStyle="{color: 'red', fontSize : '20px'}" :offset="{width: -20, height: 30}"/>
        </bm-marker>
        <bm-marker :position="tieba" animation="BMAP_ANIMATION_BOUNCE">
            <bm-label content="贴吧迎新签到点" :labelStyle="{color: 'blue', fontSize : '14px'}" :offset="{width: -38, height: 30}"/>
        </bm-marker>
        <bm-info-window :position="tieba" title="贴吧迎新活动" :show="infoWindow.show" @close="infoWindowClose" @open="infoWindowOpen">
            <p v-text="infoWindow.contents"></p>
        </bm-info-window>
    </baidu-map>
      <Tooltip placement="left" content="切换卫星图层" id="close-layer" class="top_left_menu_type" :always="true" :transfer="true" :disabled="toolTipDisable">
          <i class="iconfont" style="color: #795548" @click="close_layer">&#xe603;</i>
      </Tooltip>
      <Tooltip content="航拍全景" class="top_left_menu_type" id="quanjing" placement="left" :always="true" :transfer="true" :disabled="toolTipDisable">
          <a href="https://720yun.com/t/e8f2dqO6jcg?scene_id=1106286"><img src="./assets/p.png" height="29" alt="航拍"></a>
      </Tooltip>
      <Tooltip content="加入贴吧官方新生群" class="top_left_menu_type" id="QQ" placement="left" :always="true" :transfer="true" :disabled="toolTipDisable" >
          <img src="./assets/qq.png" height="28" alt="QQ群"  @click="QQqunModol = true">
          <!--<p>贴吧官方新生群：808843028</p>-->
      </Tooltip>
    <toolbar v-on:changNavBychild="changNavBychild" v-on:showPoint="showPoint" v-on:changeCenter="changeCenter"></toolbar>
      <div id="bottom"></div>
      <Modal v-model="QQqunModol">
          <p slot="header" style="text-align:center">
              <span>广科大贴吧2018新生群</span>
          </p>
          <div style="text-align:center">
              <img src='./assets/qun.jpg' style="width: 200px;">
              <p style="font-size: 20px; color: red">群号：808843028</p>
          </div>
          <div slot="footer">
              <Button type="default" size="large" long  @click="join_QQqun">确认</Button>
          </div>
      </Modal>

  </div>
</template>

<script>
// import 'iview/dist/styles/iview.css';
import Toolbar from './components/toolbar'
import {Tooltip, Modal, Button} from "iview"

// tileUrlTemplate="tiles/{Z}/tile{X}_{Y}.png"
// 中点坐标: 109.452338,24.335764

export default {
  name: 'app',
    components: {Toolbar, Tooltip, Modal, Button},
    data(){
      return{
          centerPoint:{lng: 109.452338, lat: 24.335764},
          zoom:16,
          clientHeight: 0,
          locPostion:{
              width:10,
              height:10
          },
          start:"",
          end:"",
          isNav:false,
          isWaPian:true,
          isShowPoint:false,
          showPonit:{
              lng:0,
              lat:0
          },
          showPonitName:"",
          toolTipDisable:false,
          QQqunModol:false,
          infoWindow: {
              show: true,
              contents: '快来签到送精美小礼品！'
          },
          tieba:{lat: 24.332636,lng: 109.455316}
      }
    },
    mounted(){
      this.clientHeight =  `${document.documentElement.clientHeight}`;
        window.onresize = function temp() {
            this.clientHeight = `${document.documentElement.clientHeight}`;
        };
        this.colseToolTips();
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
        },
        close_layer(){
            // 关闭瓦片地图
            if (this.isWaPian){
                this.isWaPian = false;
            } else{
                this.isWaPian = true;
            }
        },
        get_point(e){
            // 获取坐标
            console.log(e.point);
            // alert(point);
        },
        showPoint(point, name){
            this.showPonit = point;
            this.centerPoint = point;
            this.zoom = 17;
            this.showPonitName = name;
            this.isShowPoint = true;
        },
        changeCenter(){
            this.centerPoint = this.tieba;
        },
        colseToolTips(){
            // 5秒后隐藏
            setTimeout(this.setToolTipsFalse, 5000);
        },
        setToolTipsFalse(){
            this.toolTipDisable = "disabled";
        },
        join_QQqun(){
            if (this.QQqunModol){
                this.QQqunModol = false;
            } else{
                this.QQqunModol = false;
            }

        },
        infoWindowClose (e) {
            this.infoWindow.show = false
        },
        infoWindowOpen (e) {
            this.infoWindow.show = true
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
  @font-face {
      font-family: 'iconfont';  /* project id 829567 */
      src: url('//at.alicdn.com/t/font_829567_q760qhwhmk.eot');
      src: url('//at.alicdn.com/t/font_829567_q760qhwhmk.eot?#iefix') format('embedded-opentype'),
      url('//at.alicdn.com/t/font_829567_q760qhwhmk.woff') format('woff'),
      url('//at.alicdn.com/t/font_829567_q760qhwhmk.ttf') format('truetype'),
      url('//at.alicdn.com/t/font_829567_q760qhwhmk.svg#iconfont') format('svg');
  }

  .iconfont{
      font-family:"iconfont" !important;
      font-size:18px;font-style:normal;
      -webkit-font-smoothing: antialiased;
      -webkit-text-stroke-width: 0.2px;
      -moz-osx-font-smoothing: grayscale;}
  .top_left_menu_type{
      width: 32px;
      height: 32px;
      cursor: pointer;
      position: absolute;
      margin: 0px;
      box-sizing: border-box;
      border: 1px solid #d9d7d5;
      border-radius: 3px;
      -webkit-box-shadow: 1px 1px 1px rgba(0,0,0,.2);
      overflow: hidden;
      text-align: center;
      background: #f7f7f7;
  }
    #close-layer{
        right: 12px;
        top: 62px;
        padding-top: 2px;
    }
    #quanjing{
        right: 12px;
        top: 102px;
    }
    #QQ{
        right: 12px;
        top:142px;
        padding-top: 2px;
    }
    .vueBox{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        z-index: 10;
        height: 30px;
        overflow: hidden;
        background: #fff;
    }
  #app > div.toolbar > div:nth-child(2) > div.ivu-select-dropdown > ul{
      height: 300px;
      overflow-y: scroll;
  }
</style>
