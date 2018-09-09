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
        <Dropdown placement="top" trigger="click">
            <Button>
                <i class="iconfont" style="color: red">&#xe610;</i>
                新生导航
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem>驴打滚</DropdownItem>
                <DropdownItem>炸酱面</DropdownItem>
                <DropdownItem disabled>豆汁儿</DropdownItem>
                <DropdownItem>冰糖葫芦</DropdownItem>
                <DropdownItem divided>北京烤鸭</DropdownItem>
            </DropdownMenu>
        </Dropdown>
        <Dropdown placement="top" trigger="click">
            <Button>
                <i class="iconfont" style="color: #2196F3">&#xe651;</i>
                学生公寓
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem>驴打滚</DropdownItem>
                <DropdownItem>炸酱面</DropdownItem>
                <DropdownItem disabled>豆汁儿</DropdownItem>
                <DropdownItem>冰糖葫芦</DropdownItem>
                <DropdownItem divided>北京烤鸭</DropdownItem>
            </DropdownMenu>
        </Dropdown>
        <Dropdown placement="top" trigger="click">
            <Button>
                <i class="iconfont" style="color: #ffc107">&#xe600;</i>
                教学实验
            </Button>
            <DropdownMenu slot="list">
                <DropdownItem>驴打滚</DropdownItem>
                <DropdownItem>炸酱面</DropdownItem>
                <DropdownItem disabled>豆汁儿</DropdownItem>
                <DropdownItem>冰糖葫芦</DropdownItem>
                <DropdownItem divided>北京烤鸭</DropdownItem>
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
                <DropdownItem divided name="" style="color: red">关闭路径规划</DropdownItem>
            </DropdownMenu>
        </Dropdown>
        <Anchor class="more-nav ivu-btn ivu-btn-dashed" affix="false" v-if="isNav">
            <AnchorLink href="#bottom" title="查看更多路线" />
        </Anchor>
    </div>
</template>

<script>
    import {Button, Dropdown, DropdownMenu, DropdownItem, Anchor, AnchorLink} from 'iview'
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
          isNav:false
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
        AnchorLink
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
        more_nav(){

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
        src: url('//at.alicdn.com/t/font_829567_4th9fztjgny.eot');
        src: url('//at.alicdn.com/t/font_829567_4th9fztjgny.eot?#iefix') format('embedded-opentype'),
        url('//at.alicdn.com/t/font_829567_4th9fztjgny.woff') format('woff'),
        url('//at.alicdn.com/t/font_829567_4th9fztjgny.ttf') format('truetype'),
        url('//at.alicdn.com/t/font_829567_4th9fztjgny.svg#iconfont') format('svg');
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
    .toolbar i{
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
