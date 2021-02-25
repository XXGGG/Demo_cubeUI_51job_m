<template>
<div>
  <div class="pageTop">
    <div class="goApp" v-if="show_goApp">
      <em class="close" @click="show_goApp = false" ></em>
      <div class="in">
        <p class="tt">使用App，求职更轻松</p>
        <p class="c_gary">前程无忧 51Job APP</p>
      </div>
      <a href="https://app.51job.com/?c=h5app13" class="but">打开</a>
    </div>
  </div>

  <div class="pageContent">
    <header :class="headerTop ? 'fixed':''">
      <a href="https:/m.51job.com/" v-if="!headerTop">
        <img class="logo" src="https://img01.51jobcdn.com/im/m/logo.png" alt="">
      </a>
      <div class="btnbox" >
        <span class="location"><i>广州</i></span>
        <div class="btn">输入职位名</div>
      </div>
      <a href="" class="my" >登录</a>
    </header>

    <div class="hban">
      <!-- <cube-slide :data='items'/> -->
      <cube-slide ref="slide" :data="items">
        <cube-slide-item v-for="(item, index) in items" :key="index">
          <a :href="item.url">
            <img :src="item.image">
          </a>
        </cube-slide-item>
      </cube-slide>

      <nav class="hnav">
        <a href="https://m.51job.com/search/nearbyjoblist.php" class="a1">附近职位</a>
        <a href="https://m.51job.com/my/applyhistory.php" class="a2">申请记录</a>
        <a href="https://m.51job.com/my/whosawrsm.php" class="a3">谁看过我</a>
        <a href="https://m.51job.com/resume/myresume.php" class="a4">我的简历</a>
        <a href="https://m.51job.com/my/servicelist.php?productid=optimizeresume&mark=jlyh_H5top" class="a5">优化简历</a>
      </nav>
    </div>

    <div class="hbox">
      <div class="ht">
        <span>为你推荐</span>
        <a href="">查看全部</a>
      </div>
      <div class="list">
        <div class="stab">
          <a href="">网站前端</a>
          <a href="">前端开发</a>
          <a href="">JS开发工程师</a>
          <a href="">Web 开发工程师</a>
          <a href="">PHP</a>
          <a href="">Javascript</a>
          <a href="">HTML5</a>
        </div>
        <a href="" class="e" v-for="(i,index) in homeList" :key="index">
          <i>{{i.salary}}</i>
          <strong>
            <span>前端开发工程师</span>
          </strong>
          <em>{{i.site}}</em>
          <p>{{i.condition}}</p>
          <div class="tabs">
            <span class="f1" v-for="(x,xx) in i.welfare" :key="xx">{{x}}</span>
          </div>
          <button class="btn jobid">申请</button>
          <span class="aside">{{i.aside}}</span>
        </a>
      </div>
      <a href="" class="more">更多推荐职位</a>
    </div>
    
    <div class="hbox">
      <div class="ht">
        <span>求职服务</span>
      </div>
      <div class="hser">
        <a href="" class="a1">
          <img src="//img01.51jobcdn.com/im/mkt/m/xszc/button_0821_1.png" alt="">
        </a>
        <a href="" class="a2">
          <img src="https://img01.51jobcdn.com/im/mkt/m/xszc/button_0821_2.png" alt="">
        </a>
        <a href="" class="a3">
          <i>无忧学院</i>
        </a>
        <a href="" class="a4">
          <i>校园招聘</i>
        </a>
        <a href="" class="a5">
          <i>求职攻略</i>
        </a>
        <a href="" class="a6">
          <i>简历模板</i>
        </a>
      </div>
      <div class="hinf">
        <a href="" class="at"  v-for="(i,index) in hinfList" :key="index">{{i.text}}</a>
      </div>

      <cube-tab-bar v-model="selectedLabel" show-slider>
        <cube-tab v-for="(item) in tabs"  :label="item.label" :key="item.label">
        </cube-tab>
      </cube-tab-bar>
      <cube-tab-panels v-model="selectedLabel">
          <cube-tab-panel v-for="(item) in tabs" :label="item.label" :key="item.label">
              <a class="tab-panel-li" v-for="(hero) in item.heroes" :key="hero">
                {{hero}}
              </a>
          </cube-tab-panel>
      </cube-tab-panels>
    </div>
    <a href="javascript:scrollTo(0,0);" class="goTop" v-if="show_goTop">TOP</a>
  </div>

  <div class="pageFooter">
    <footer>
      <p class="icons">
        <a href="" class="app">APP下载</a>
        <a href="" class="wx">微信公众号</a>
        <a href="" class="pc">电脑版</a>
      </p>
      <p class="c_666">
        <a href="">使用帮助</a>|
        <a href="">用户反馈</a>|
        <a href="">企业入口</a>|
        <a href="">职场百科</a>
      </p>
      <p>
        无忧工作网版权所有©1999-2021
        <br>
        51job.com（沪ICP备12015550）
      </p>
    </footer>
  </div>
</div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
  },
  data() {
    return {
      headerTop:false,
      show_goTop:false,
      show_goApp:true,
      items: [
        {
          url: 'https://m.51job.com/',
          image: '//img01.51jobcdn.com/im/mkt/m/supplement/yuanxiao_ban_2021.png'
        },
        {
          url: 'https://m.51job.com/',
          image: '//img01.51jobcdn.com/im/mkt/tg/lp_wx128/686_240.jpg'
        },
        {
          url: 'https://m.51job.com/',
          image: '//img01.51jobcdn.com/im/pm/jinying/banner20210105/686-240.png'
        },
        {
          url: 'https://m.51job.com/',
          image: '//img01.51jobcdn.com/im/mkt/tg/2021banner/jlhd/686_240.jpg'
        },
        {
          url: 'https://m.51job.com/',
          image: '//img01.51jobcdn.com/im/mkt/tg/2021banner/dk_ztc/686_240.jpg'
        },
      ],
      homeList:[
        {
          "salary":"4.5-7.5千/月",
          "site":"广州-增城区",
          "name":"前端开发工程师",
          "condition":"民营公司 | 大专 | 2年",
          "welfare":["五险一金","员工旅游","专业培训","定期体验"],
          "aside":"华商教育集团"
        }
      ],
      hinfList:[
        {"text":"现时特惠，升级简历助你入职涨薪"},
        {"text":"面试失败了，改追问HR原因吗？"},
        {"text":"用无忧精英APP，线上找猎头"},
        {"text":"美术艺考考什么"},
        {"text":"总务是做什么的"},
      ],
      selectedLabel: '热门职位',
      tabs: [{
        label: '热门职位',
        heroes: [
          "广州计算机软件1",
          "广州代驾招聘2",
          "广州计算机软件3",
          "广州代驾招聘4",
          "广州计算机软件5",
          "广州代驾招聘6",
          "广州计算机软件7",
          "广州代驾招聘8",
          "广州计算机软件9",
          "广州代驾招聘0",
        ]
      }, {
        label: '热门城市',
        heroes: [
          "上海人才招聘",
          "佛山人才招聘",
          "北京人才招聘",
          "顺德人才招聘",
          "深圳人才招聘",
          "东莞人才招聘",
          "广州人才招聘",
          "中山人才招聘",
          "武汉人才招聘",
          "江门人才招聘",
        ]
      }, {
        label: '职位百科',
        heroes: [
          "广州计算机软件人才",
        ]
      }, {
        label: '简历模板',
        heroes: [
          "广州计算机软件人才",
          "广州代驾招聘",
        ]
      }],
    }
  },
  created(){
    this.getHomeList();
  },
  mounted(){
      window.addEventListener('scroll',this.go_scroll)
  },
  methods:{
    getHomeList(){
      this.axios.get('mock/homeList.json').then(res=>{
        // console.log(res)
        this.homeList = res.data.homeList
      })
    },
    go_scroll(e){
      let top = document.documentElement.scrollTop //距离顶部
      // console.log(top)
      if(this.show_goApp && top >= 80){
        this.headerTop = true;
      }else if(!this.show_goApp && top >= 1){
        this.headerTop = true;
      }else{
        this.headerTop = false
      }
      if(top>1000){
        this.show_goTop = true
      }else{
        this.show_goTop = false
      }
    }
  },
  beforeRouteLeave(to,from,next){
    this.$destroy();
    next();
  },
  destroyed() {
    window.removeEventListener('scroll',this.go_scroll)
  }
}
</script>

<style lang="scss" scoped>
.goApp{
  height: 74px;
  background-color: #eee;
  display: flex;
  align-items: center;
  justify-content: space-between;
  line-height: 20px;
  padding-right: 16px;
  .close{
    width: 42px;
    height: 100%;
    background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABMAAAASBAMAAABLIvhaAAAAJ1BMVEUAAACZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmahP7BAAAADHRSTlMAFNBr5Mi+vXdWMQ+YXasMAAAAZklEQVQI1yXNqw2AQBRE0SEbEGAIBo1HUAAlUAQt0AkeQy18khUURebdVZOT7H2qN8U7pOpqvdIrFePgOd+SOnP6JgWDcCBshB8jvGSGv9N2M9OOptscijYYbVDBIFwazauanU5//miIGyc+P6v9AAAAAElFTkSuQmCC) 50% no-repeat;
    background-size: 10px auto;
  }
  .in{
    flex:1;
    padding:17px 0 17px 70px;
    background: url(data:image/png;base64,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) 0 no-repeat;
    background-size: 55px auto;
  }
  .tt{
    font-size: 16px;
  }
  .c_gary{
    font-size:12px;
    color:#999;
  }
  .but{
    width: 72px;
    height: 28px;
    line-height: 28px;
    color:#0f81fe;
    background-color: #e4e4e6;
    border-radius: 28px;
    text-align: center;
  }
}
.fixed{
  position: fixed;
  top:0;
  padding: 0 56px 0 16px;
  z-index: 10;
}
header{
  position: relative;
  transition: all .3s;
  width: 100%;
  height: 60px;
  line-height: 60px;
  color: #222;
  padding: 0 56px 0 96px;
  background-color: #fff;
  box-sizing: border-box;
  a{
    text-decoration: none;
    .logo{
      width: 68px;
      position: absolute;
      left: 16px;
    }
  }
  .btnbox{
    position: relative;
    height: 20px;
    line-height: 20px;
    padding-left: 92px;
    border:6px solid #eee;
    background-color: #eee;
    border-radius: 20px;
    .location{
      position: absolute;
      left: 0;
      top: 0;
      width: 75px;
      height: 20px;
      font-size: 0;
      text-align: center;
      border-right: 1px solid #999;
      i{
        display: inline-block;
        max-width: 4em;
        font-size: 14px;
        color: #222;
        text-align: center;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
        padding-right: 8px;
        
      }
    }
    .location:after{
      content:"\00a0";
      display: inline-block;
      width: 7px;
      vertical-align: top;
      background-position: -200px 0;
    }
    .btn:before{
      content:'\00a0';
      display: inline-block;
      width: 16px;
      vertical-align: top;
      margin-right: 8px;
      background-position: -175px 0;
    }
    .btn{
      color:#999
    }
  }
  .btnbox, 
  .logo{
      top: 50%;
      transform: translateY(-50%);
  }
  .my{
    position:absolute;
    top:50%;
    right:16px;
    width: 28px;
    height: 28px;
    line-height: 28px;
    font-size: 0;
    color: #ff7e3e;
    background-position: 0 0;
    transform:translateY(-50%);
  }
}
.hban{
  /* max-width: 500px; */
  margin-bottom: 8px;
  padding:0 16px;
  box-sizing: border-box;
  background-color: #fff;
  img{
    width:100%;
  }
  .hnav{
    position: relative;
    padding: 0;
    display: flex;
    justify-content: space-between;
    line-height: 38px;
    a{
      height: 96px;
      position: relative;
      line-height: 136px;
      font-size: 12px;
      color: #666;
    }
    a::before{
      content:'\00a0';
      position: absolute;
      width: 48px;
      height: 34px;
      top: 20px;
      left: 50%;
      background-size: 250px auto;
      transform:  translateX(-50%);
    }
    .a1::before{
      background-position: 0 0;
    }
    .a2::before{
      background-position: -50px 0;
    }
    .a3::before{
      background-position: -100px 0;
    }
    .a4::before{
      background-position: -150px 0;
    }
    .a5::before{
      background-position: -200px 0;
    }
  }
}
.hbox{
  margin-bottom: 8px;
  background-color: #fff;
  .ht{
    width: 100%;
    box-sizing: border-box;
    line-height: 56px;
    padding: 0 16px;
    a{
    float:right;
    font-size: 14px;
    color: #666;
    &:after{
      content: '\00a0';
      display: inline-block;
      width: 6px;
      vertical-align: top;
      margin-left: 6px;
      background-position: -225px 11px !important;
    }
  }
    span{
      font-size: 18px;
      font-weight: 700;
    }
  }
  .ht, .ht span{
    position: relative;
    height: 56px;
    display: inline-block;
    font-size: 18px;
    font-weight: 700;
  }
  
}
.list{
  background-color: #fff;
  .stab{
    max-height: 84px;
    overflow: hidden;
    padding:0 8px 0 16px;
    a{
      float: left;
      max-width: 100%;
      height:28px;
      line-height:28px;
      color: #666;
      margin: 0 8px 14px 0;
      padding: 0 12px;
      background-color:#f5f5f5;
      border-radius: 28px;
      font-size: 14px;
      text-align: center;
    }
  }
  .e{
    width: 100%;
    box-sizing: border-box;
    display: block;
    position: relative;
    line-height: 20px;
    padding: 14px 16px;
    &:before{
      content:'\00a0';
      position: absolute;
      top:0;
      right: 16px;
      left: 16px;
      height: 1px;
      background-color: #f0f0f0;
    }
    i{
      font-weight: 700;
      color: #ff7e3e;
    }
    strong{
      display: block;
      font-weight: 700;
      font-size: 16px;
      color: #222;
      span{
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
      }
    }
    .tabs{
      overflow: hidden;
      .f1{
        background-color: #fff;
      }
      span{
        float:left;
        height: 20px;
        line-height: 18px;
        margin-right: 8px;
        padding:0 3px;
        border: 1px solid #e2e2e2;
        border-radius: 4px;
        box-sizing: border-box;
      }
    }
    .btn{
      width: 70px;
      height: 30px;
      line-height: 30px;
      font-weight: 700;
      color: #ff7e3e;
      text-align: center;
      background-color: #ffe8dc;
      border-radius: 30px;
      float: right;
      margin-left: 10px;
      outline: 0;
      border:0;
      padding:0;
    }
    .aside{
      height: 30px;
      line-height: 30px;
      color: #222;
    }
  }
}
.list .e em,
.list .e i{
  float: right;
  width: 100px;
  text-align: right;
  margin-left: 10px;
}
.list .e .tabs span,
.list .e em,
.list .e p{
  display: block;
  font-size: 12px;
  color: #666;
}
.list .e .tabs,
.list .e em,
.list .e p{
  margin: 8px 0;
}
.more{
  width: 100%;
  box-sizing: border-box;
  position: relative;
  display: block;
  height: 48px;
  line-height: 48px;
  color: #666;
  text-align: center;
  &:before{
    content: "\00a0";
    position: absolute;
    top: 0;
    right: 16px;
    left: 16px;
    height: 1px;
    background-color: #f0f0f0;
  }
  &:after{
    content: "\00a0";
    display: inline-block;
    width: 6px;
    vertical-align: top;
    margin-left: 6px;
    margin-top:-4px ;
    background-position: -225px 11px !important;
  }
}
.hser{
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 0 16px;
  a{
    width: 24%;
    height: 96px;
    text-align: center;
    padding-top: 12px;
    background: #fafafa no-repeat bottom;
    background-size: 80px auto;
    box-sizing: border-box;
  }
  .a1, .a2{
    width: 49%;
    margin-bottom: 6px;
  }
  img{
    width: 100%;
  }
  i{
    color: #222;
    font-weight: 400;
    font-style: normal;
  }
  .a3{
        background-image: url(data:image/png;base64,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);
  }
  .a4{
        background-image: url(data:image/png;base64,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);
  }
  .a5{
    background-image: url(data:image/png;base64,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);
  }
  .a6{
        background-image: url(data:image/png;base64,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);
  }
}
.hinf{
  overflow: hidden;
  padding: 5px 0;
  a{
    position: relative;
    display: block;
    height: 30px;
    line-height: 30px;
    font-size: 16px;
    color: #333;
    margin: 10px 0;
    padding: 0 16px 0 36px;
    &:before{
      content: "\00a0";
      position: absolute;
      left: 16px;
      top: 0;
      width: 12px;
      background-position: -150px 5px;
    }
  }
}
.tab-panel-li{
  position: relative;
  float: left;
  width: 50%;
  height: 24px;
  line-height: 24px;
  color: #222;
  margin: 5px 0;
  padding: 0 8px 0 30px;
  box-sizing: border-box;
  &:before{
        content: "\00a0";
    position: absolute;
    left: 16px;
    top: 50%;
    width: 6px;
    height: 6px;
    background-color: #ffcbb1;
    border-radius: 100%;
    transform: translateY(-50%);
  }
}

/* footer */
footer{
  padding: 16px 0;
  font-size: 12px;
  text-align: center;
  color: #999;
  line-height: 20px;
  .icons{
    display: flex;
    justify-content: space-evenly;
    margin-bottom: 20px;
    a{
      display: inline-block;
      width: 5.5em;
      color: #999;
      &:before {
        content: "\00a0";
        display: block;
        width: 30px;
        height: 30px;
        margin: 0 auto 6px;
      }
    }
    .app::before{
      background-position: -50px 0;
    }
    .wx::before{
      background-position: -100px 0;
    }
    .pc::before{
      background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAMAAAANIilAAAAAh1BMVEUAAABHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPNHsPP////d8P11xPap0+7U6vheuvVqv/Xz+v5VtvTm9P3P6vyu3Prp9PzG5/ub1Plrv/XE4fNb4mq5AAAAG3RSTlMA/MMbFQ/vybSolXJVSEE+BtB8877jrqXffeSxb0XHAAABrklEQVRIx6WX6XaCMBBGk5RNEVxwaz+sRRDc3v/5KoQciWgMyf0JuedkmUlmyGvcaDHyVwmQrPzRInKJNl8ho5CgLPzSUqeBMGU/mH5UY4a3sFg94Q2UbBSTn3j4gDd5o87G0GA8e3k6S2jBnL7r+NBk3rPdOaBtu0/rXWIAS3ndYwxiLJ0RBjLpxIaHgXiPaFmDc6jKnZqyOqBhLdwYnCrVoUKDiPM2Fy6pHhceK20OgpNryjkaeIYGaMjqH6c/Nad6UIaaoHYd2pH3ULOvB/E9o3WUhjCTEfLtMpMZIS41lalLIpjKiMjCXP4mI3N5RHxz2Scrc/mHJOZyQmAuw0amNtP2bDZsa3VUVkFiF55yYtyg5iYlxiMli1SXQqTk4zJAqemW4LDONYQs13LzDJyQX4DCPmu4Z+FSp716BcWvxPE++Ch/KiAIpEu/z+4u7/CGtixjJjITD52JHMtPrMy1s+YreqxVj3uWdsn6j7uqrCjy7tEWeGJiU9BYlFJsRiScOWBSAgpb37UpXG1LZvti3b5NsG9Q7Fsj0ZT59Mn0NZoyuR3cepR6W0U7+A+zkixuFCPdzQAAAABJRU5ErkJggg==);
    -webkit-background-size: 30px auto;
    -moz-background-size: 30px auto;
    -o-background-size: 30px auto;
    -ms-background-size: 30px auto;
    background-size: 30px auto;
    }
  }
  .c_666{
    font-size: 14px;
    color: #666;
    margin-bottom: 20px;
    a{
      display: inline-block;
      width: 5.5em;
    }
  }
}
.goTop{
  position: fixed;
  right: 11px;
  bottom: 60px;
  z-index: 3;
  width: 40px;
  height: 40px;
  line-height: 50px;
  font-size: 12px;
  color: #fff2e3;
  text-align: center;
  background-color: #b2a99e;
  border-radius: 100%;
  &:after{
    content: "\00a0";
    position: absolute;
    left: 50%;
    top: 5px;
    width: 0;
    height: 0;
    margin-left: -10px;
    border-right: 10px solid transparent;
    border-left: 10px solid transparent;
    border-bottom: 10px solid #fff2e3;
  }
}
</style>
