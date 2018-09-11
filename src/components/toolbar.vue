<template>
    <div class="toolbar">
        <!--<ul class="toolbar-ul">-->
            <!--<li>-->
                <!--<Dropdown placement="top">-->
                    <!--<Button>-->
                        <!--<i class="iconfont" style="color: red">&#xe610;</i>-->
                        <!--新生导航-->
                    <!--</Button>-->
                    <!--<DropdownMenu slot="list">-->
                        <!--<DropdownItem>驴打滚</DropdownItem>-->
                        <!--<DropdownItem>炸酱面</DropdownItem>-->
                        <!--<DropdownItem disabled>豆汁儿</DropdownItem>-->
                        <!--<DropdownItem>冰糖葫芦</DropdownItem>-->
                        <!--<DropdownItem divided>北京烤鸭</DropdownItem>-->
                    <!--</DropdownMenu>-->
                <!--</Dropdown>-->
            <!--</li>-->
            <!--<li>-->
                <!--<Button>-->
                    <!--<i class="iconfont" style=" color: #2196F3; ">&#xe651;</i>-->
                    <!--学生公寓-->
                <!--</Button>-->
            <!--</li>-->
            <!--<li>-->
                <!--<Button>-->
                    <!--<i class="iconfont" style=" color: #ffc107; ">&#xe600;</i>-->
                    <!--教学实验-->
                <!--</Button>-->
            <!--</li>-->
            <!--<li>-->
                <!--<Button>-->
                    <!--<i class="iconfont" style=" color: #4caf50; ">&#xe61b;</i>-->
                    <!--路径规划-->
                <!--</Button>-->
            <!--</li>-->
        <!--</ul>-->
        <Dropdown placement="top" trigger="click" @on-click="draw_point">
            <Button>
                <i class="iconfont" style="color: red">&#xe610;</i>
                新生导航
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem name="freshman">报到点</DropdownItem>
                <DropdownItem name="teiba">贴吧签到点</DropdownItem>
            </DropdownMenu>
        </Dropdown>
        <Dropdown placement="top" trigger="click" @on-click="draw_point">
            <Button>
                <i class="iconfont" style="color: #2196F3">&#xe651;</i>
                学生公寓
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem name="nan_1">南1#</DropdownItem>
                <DropdownItem name="nan_2">南2#</DropdownItem>
                <DropdownItem name="nan_3">南3#</DropdownItem>
                <DropdownItem name="nan_4">南4#</DropdownItem>
                <DropdownItem name="nan_5">南5#</DropdownItem>
                <DropdownItem name="nan_6">南6#</DropdownItem>
                <DropdownItem name="nan_7">南7#</DropdownItem>
                <DropdownItem name="nan_8">南8#</DropdownItem>
                <DropdownItem name="nan_9">南9#</DropdownItem>
                <DropdownItem name="nan_10">南10#</DropdownItem>
                <DropdownItem name="nan_11">南11#</DropdownItem>
                <DropdownItem name="nan_12">南12#</DropdownItem>
                <DropdownItem name="bei_1">北1#</DropdownItem>
                <DropdownItem name="bei_2">北2#</DropdownItem>
                <DropdownItem name="bei_3">北3#</DropdownItem>
                <DropdownItem name="bei_4">北4#</DropdownItem>
                <DropdownItem name="bei_5">北5#</DropdownItem>
                <DropdownItem name="bei_6">北6#</DropdownItem>
                <DropdownItem name="bei_7">北7#</DropdownItem>
                <DropdownItem name="bei_8">北8#</DropdownItem>
                <DropdownItem name="bei_9">北9#</DropdownItem>
                <DropdownItem name="bei_10">北10#</DropdownItem>
                <DropdownItem name="bei_11">北11#</DropdownItem>
                <DropdownItem name="bei_12">北12#</DropdownItem>
                <DropdownItem name="bei_13">北13#</DropdownItem>
                <!--<DropdownItem>-->
                    <!--<Dropdown placement="top" @on-click="draw_point">-->
                        <!--<DropdownItem>-->
                            <!--南区-->
                            <!--<Icon type="ios-arrow-forward"></Icon>-->
                        <!--</DropdownItem>-->
                        <!--<DropdownMenu slot="list">-->
                            <!--<DropdownItem name="nan_1">南1#</DropdownItem>-->
                            <!--<DropdownItem name="nan_2">南2#</DropdownItem>-->
                            <!--<DropdownItem name="nan_3">南3#</DropdownItem>-->
                            <!--<DropdownItem name="nan_4">南4#</DropdownItem>-->
                            <!--<DropdownItem name="nan_5">南5#</DropdownItem>-->
                            <!--<DropdownItem name="nan_6">南6#</DropdownItem>-->
                            <!--<DropdownItem name="nan_7">南7#</DropdownItem>-->
                            <!--<DropdownItem name="nan_8">南8#</DropdownItem>-->
                            <!--<DropdownItem name="nan_9">南9#</DropdownItem>-->
                            <!--<DropdownItem name="nan_10">南10#</DropdownItem>-->
                            <!--<DropdownItem name="nan_11">南11#</DropdownItem>-->
                            <!--<DropdownItem name="nan_12">南12#</DropdownItem>-->
                        <!--</DropdownMenu>-->
                    <!--</Dropdown>-->
                <!--</DropdownItem>-->
                <!--<DropdownItem>-->
                    <!--<Dropdown placement="top" @on-click="draw_point">-->
                        <!--<DropdownItem>-->
                            <!--北区-->
                            <!--<Icon type="ios-arrow-forward"></Icon>-->
                        <!--</DropdownItem>-->
                        <!--<DropdownMenu slot="list">-->
                            <!--<DropdownItem name="bei_1">北1#</DropdownItem>-->
                            <!--<DropdownItem name="bei_2">北2#</DropdownItem>-->
                            <!--<DropdownItem name="bei_3">北3#</DropdownItem>-->
                            <!--<DropdownItem name="bei_4">北4#</DropdownItem>-->
                            <!--<DropdownItem name="bei_5">北5#</DropdownItem>-->
                            <!--<DropdownItem name="bei_6">北6#</DropdownItem>-->
                            <!--<DropdownItem name="bei_7">北7#</DropdownItem>-->
                            <!--<DropdownItem name="bei_8">北8#</DropdownItem>-->
                            <!--<DropdownItem name="bei_9">北9#</DropdownItem>-->
                            <!--<DropdownItem name="bei_10">北10#</DropdownItem>-->
                            <!--<DropdownItem name="bei_11">北11#</DropdownItem>-->
                            <!--<DropdownItem name="bei_12">北12#</DropdownItem>-->
                            <!--<DropdownItem name="bei_13">北13#</DropdownItem>-->
                        <!--</DropdownMenu>-->
                    <!--</Dropdown>-->
                <!--</DropdownItem>-->
            </DropdownMenu>
        </Dropdown>
        <Dropdown placement="top" trigger="click"  @on-click="draw_point">
            <Button>
                <i class="iconfont" style="color: #ffc107">&#xe600;</i>
                教学实验
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem name="teach_1">第一教学楼</DropdownItem>
                <DropdownItem name="teach_2">第二教学楼</DropdownItem>
                <DropdownItem name="teach_3">第三教学楼</DropdownItem>
                <DropdownItem name="teach_4">第四教学楼</DropdownItem>
                <DropdownItem name="teach_5">第五教学楼</DropdownItem>
                <DropdownItem name="teach_6">第六教学楼</DropdownItem>
                <DropdownItem name="teach_7">基础实验楼</DropdownItem>
                <DropdownItem name="teach_8">图书馆</DropdownItem>
                <DropdownItem name="teach_9">行政楼</DropdownItem>
            </DropdownMenu>
        </Dropdown>
        <Dropdown placement="top" trigger="click" @on-click="nav">
            <Button>
                <i class="iconfont" style="color: #4caf50">&#xe61b;</i>
                路径规划
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem name="火车站-东环校区">火车站-东环校区</DropdownItem>
                <DropdownItem name="火车站-柳石校区">火车站-柳石校区</DropdownItem>
                <DropdownItem divided name="汽车站-东环校区">汽车站-东环校区</DropdownItem>
                <DropdownItem name="汽车站-柳石校区">汽车站-柳石校区</DropdownItem>
                <DropdownItem divided name="飞机场-东环校区">飞机场-东环校区</DropdownItem>
                <DropdownItem name="飞机场-柳石校区">飞机场-柳石校区</DropdownItem>
                <DropdownItem divided name="" v-if="isNav" style="color: red">关闭路径规划</DropdownItem>
            </DropdownMenu>
        </Dropdown>
        <Anchor class="more-nav ivu-btn ivu-btn-dashed" affix="false" v-if="isNav">
            <AnchorLink href="#bottom" title="查看更多路线" />
        </Anchor>
    </div>
</template>

<script>
    import {Button, Dropdown, DropdownMenu, DropdownItem, Anchor, AnchorLink, Icon} from 'iview'
export default {
  name: 'toolbar',
    data(){
      return {
        huochezhan: {
            lng:109.393776,
            lat:24.315026
        },
          gxust:{
            lng:109.453324,
              lat:24.336022
          },
          feijichang:{
            lng:109.410643,
              lat:24.20709
          },
          qichezhan:{
            lng:109.403271,
              lat:24.310501
          },
          liushi:{
            lng:109.447001,
              lat:24.249786
          },
          isNav:false,
          nanqu:[
              {
                lng: 109.455379,
                  lat:24.337027,
                  name:"南1#"
              },
              {
                  lng: 109.455572,
                  lat:24.336731,
                  name:"南2#"
              },
              {
                  lng: 109.454768,
                  lat:24.336756,
                  name:"南3#"
              },
              {
                  lat: 24.337287,
                  lng: 109.455244,
                  name:"南4#"
              },
              {
                  lat: 24.337003,
                  lng: 109.454494,
                  name:"南5#"
              },
              {
                  lat: 24.336752,
                  lng: 109.454193,
                  name:"南6#"
              },
              {
                  lat: 24.336418,
                  lng: 109.454934,
                  name:"南7#"
              },
              {
                  lat: 24.336143,
                  lng: 109.454979,
                  name:"南8#"
              },
              {
                  lat: 24.33613,
                  lng: 109.455617,
                  name:"南9#"
              },
              {
                  lat: 24.336447,
                  lng: 109.455621,
                  name:"南10#"
              },
              {
                  lat: 24.336431,
                  lng: 109.454278,
                  name:"南11#"
              },
              {
                  lat: 24.336122,
                  lng: 109.454283,
                  name:"南12#"
              }
          ],
          beiqu:[
              {
                  lat: 24.341246,
                  lng: 109.452383,
                  name:"北1#"
              },
              {
                  lat: 24.340464,
                  lng: 109.452262,
                  name:"北2#"
              },
              {
                  lat: 24.340834,
                  lng: 109.452805,
                  name:"北3#"
              },
              {
                  lat: 24.34074,
                  lng: 109.45179,
                  name:"北4#"
              },
              {
                  lat: 24.341077,
                  lng: 109.451795,
                  name:"北5#"
              },
              {
                  lat: 24.340443,
                  lng: 109.451741,
                  name:"北6#"
              },
              {
                  lat: 24.338797,
                  lng: 109.452576,
                  name:"北7#"
              },
              {
                  lat: 24.339151,
                  lng: 109.452549,
                  name:"北8#"
              },
              {
                  lat: 24.339398,
                  lng: 109.452423,
                  name:"北9#"
              },
              {
                  lat: 24.339987,
                  lng: 109.451804,
                  name:"北10#"
              },
              {
                  lat: 24.339168,
                  lng: 109.451889,
                  name:"北11#"
              },
              {
                  lat: 24.339468,
                  lng: 109.453142,
                  name:"北12#"
              },

              {
                  lat: 24.339196,
                  lng: 109.453155,
                  name:"北13#"
              }
          ],
          freshman:{
              name:"报到点",
              lat: 24.333797,
              lng: 109.455294
          },
          teach:[
              {
                  lat: 24.339826,
                  lng: 109.448067,
                  name:"第一教学楼"
              },
              {
                  lat: 24.340768,
                  lng: 109.447927,
                  name:"第二教学楼"
              },
              {
                  lat: 24.334373,
                  lng: 109.454301,
                  name:"第三教学楼"
              },
              {
                  lat: 24.335237,
                  lng: 109.455293,
                  name:"第四教学楼"
              },
              {
                  lat: 24.333039,
                  lng: 109.456178,
                  name:"第五教学楼"
              },
              {
                  lat: 24.333011,
                  lng: 109.454368,
                  name:"第六教学楼"
              },
              {
                  lat: 24.33227,
                  lng: 109.454346,
                  name:"基础实验楼"
              },
              {
                  lat: 24.340303,
                  lng: 109.450923,
                  name:"图书馆"
              },
              {
                  lat: 24.332303,
                  lng: 109.456214,
                  name:"行政楼"
              },
          ]
      }
    },
  props: {

  },
    components:{
      Button,
        Dropdown,
        DropdownMenu,
        DropdownItem,
        Anchor,
        AnchorLink,
        Icon
    },
    methods:{
        nav(name) {
            if (name != ""){
                let arr = name.split("-");

                let start = this.getPosition(arr[0]);
                let end = this.getPosition(arr[1]);
                this.$emit("changNavBychild", start, end);
                this.isNav = true;
            } else {
                this.$emit("changNavBychild", "", "");
                this.isNav = false;
            }
        },
        getPosition(name){
            let postion = "";
            switch (name) {
                case "东环校区":
                    postion = this.gxust;
                    break;
                case "火车站":
                    postion = this.huochezhan;
                    break;
                case "汽车站":
                    postion = this.qichezhan;
                    break;
                case "飞机场":
                    postion = this.feijichang;
                    break;
                case "柳石校区":
                    postion = this.liushi;
                    break;
            }

            return postion;

        },
        draw_point(name){
            if (name == "" || name == undefined){
                return;
            }
            // 获取点
            let arr = name.split("_");
            let point = null;
            // console.log(arr[0]+","+arr[1]);
            if (arr[0] == "nan"){
                // console.log(arr[0]);
                point = this.nanqu[arr[1]-1];
            } else if (arr[0] == "bei") {
                point = this.beiqu[arr[1]-1];
            }else if(arr[0] == "freshman"){
                point = this.freshman;
            }else if(arr[0] == "teach"){
                point = this.teach[arr[1]-1];
            }else if(arr[0] == "teiba"){
                this.$emit("changeCenter");
                return;
            }
            // console.log(point);
            this.$emit("showPoint",{lat:point.lat, lng:point.lng}, point.name);
        }
    },
    mounted() {

    }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    @font-face {
        font-family: 'iconfont';  /* project id 829567 */
        src: url('//at.alicdn.com/t/font_829567_ua54dme189.eot');
        src: url('//at.alicdn.com/t/font_829567_ua54dme189.eot?#iefix') format('embedded-opentype'),
        url('//at.alicdn.com/t/font_829567_ua54dme189.woff') format('woff'),
        url('//at.alicdn.com/t/font_829567_ua54dme189.ttf') format('truetype'),
        url('//at.alicdn.com/t/font_829567_ua54dme189.svg#iconfont') format('svg');
    }

    .iconfont{
        font-family:"iconfont" !important;
        font-size:18px;font-style:normal;
        -webkit-font-smoothing: antialiased;
        -webkit-text-stroke-width: 0.2px;
        -moz-osx-font-smoothing: grayscale;}
    .toolbar{
        padding: 0;
        margin: 0;
        width: 100%;
        position: absolute;
        bottom: 0;
        left: 0;
        text-align: center;
    }
    .toolbar-ul>li{
        display: inline;
    }
    .toolbar button{
        text-align: center;
    }
    .iconfont{
        display: block;
    }
    .more-nav{
        position: absolute;
        bottom: 80px;
        left:50%;
        display: block;
        margin-left:-52px;
    }
    .ivu-anchor-link-title{
        margin-left: -14px !important;
    }
    .ivu-anchor-link:before{
        display: none !important;
    }
</style>
