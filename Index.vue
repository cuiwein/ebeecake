<template>

 <div class="app-index">
          <!--轮播图     mint-ui-->
    <mt-swipe  :auto="4000">
      <mt-swipe-item v-for="item of navlist" :key="item.id">
        <img :src="item.img_url" />
      </mt-swipe-item>
    </mt-swipe>
    <!--小轮播图-->
   <!--推荐更多图片滑动-->
    <div class="new-product-box">
      <div class="new-title">蛋糕推荐
      <img src="http://127.0.0.1:3000/ico_2.png" class="ioc">
      <span class="new-more">更多</span>
      </div>
      <div class="newBoxundefined">
        <ul class="items">
          <li class="item" v-for="item of list1">
            <router-link to="/Login">
              <img :src="item.img_url" class="new-img"/>
              <p class="new-title">{{item.title}}</p>
              <p class="new-price">￥{{item.price}}起</p>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
     <!--庆生蛋糕-->
     <div class="new-product-box">
      <div class="new-title">蛋糕推荐
      <img src="http://127.0.0.1:3000/ico_1.png" class="ioc">
      <span class="new-more">更多</span>
      </div>
      <div class="newBoxundefined">
        <ul class="items">
          <li class="item" v-for="item of list2">
            <router-link to="/Login">
              <img :src="item.img_url" class="new-img"/>
              <p class="new-title">{{item.title}}</p>
              <p class="new-price">￥{{item.price}}起</p>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
    <!--小滑动图-->
     <div>
        <ul class="small-img">
           <li class="small-li">
           <img src="http://images.ebeecake.com/img/2134.jpg" class="more">
           <p class="small-title">桃芝|樱桃芝士蛋糕</p>
           <p class="small-title">￥265起</p>
           </li>
          <li class="small-li">
           <img src="http://images.ebeecake.com/img/2059.jpg" class="more">
           <p class="small-title">回归|90回忆蛋糕</p>
           <p class="small-title">￥265起</p>
           </li>
           <li class="small-li">
           <img src="http://images.ebeecake.com/img/2875.jpg" class="more">
           <p class="small-title">初心|牛油果低脂蛋糕</p>
           <p class="small-title">￥265起</p>
           </li>
           <li class="small-li">
           <img src="http://images.ebeecake.com/img/2027.jpg" class="more">
           <p class="small-title">向往|酸樱桃椰蓉蛋糕</p>
           <p class="small-title">￥356起</p>
           </li>
           <li class="small-li">
           <img src="http://images.ebeecake.com/img/2126.jpg" class="more">
           <p class="small-title">星空|黑森林蛋糕</p>
           <p class="small-title">￥265起</p>
           </li>
           <li class="small-li">
           <img src="http://images.ebeecake.com/img/2089.jpg" class="more">
           <p class="small-title">思念|缤纷乐园蛋糕</p>
           <p class="small-title">￥325起</p>
           </li>
        </ul>
     </div>

    <!--结束-->
  </div>
</template>
<script>
export default {
   data(){
     return {
        navlist:[],//轮播图列表
        list1:[//推荐蛋糕
         {id: 1, title: "向往|酸樱桃椰蓉", img_url: "http://images.ebeecake.com/img/2027.jpg",price:225},
        {id:2, title: "相伴|奶油杏仁", img_url: "http://images.ebeecake.com/img/2198.jpg",price:189},
        {id:3, title: "皓月|浓情凝聚", img_url: "http://images.ebeecake.com/img/3833.jpg",price:356},
        {id:4, title: "珍味|沙棘任小米蛋糕", img_url: "http://images.ebeecake.com/img/3921.jpg",price:225},
        {id:5, title: "珍贵|芒果慕斯", img_url: "http://images.ebeecake.com/img/2190.jpg",price:356}],
        //庆生蛋糕
        list2:[
         {id: 1, title: "倾慕|抹茶慕斯", img_url: "http://images.ebeecake.com/img/2003.jpg",price:225},
        {id:2, title: "流连|榴莲慕斯", img_url: "http://images.ebeecake.com/img/2158.jpg",price:189},
        {id:3, title: "我愿意|玫瑰荔枝慕斯", img_url: "http://images.ebeecake.com/img/4058.jpg",price:356},
        {id:4, title: "热恋|玫瑰慕斯", img_url: "http://images.ebeecake.com/img/2182.jpg",price:225},
        {id:5, title: "迷恋|提拉米苏", img_url: "http://images.ebeecake.com/img/2230.jpg",price:356}]
     }
   },
   created() {
     this.handleImage();
   },
   methods:{
     //加载轮轮图数据
     handleImage(){
      //1:发送ajax获取轮播数据
      var url = "http://127.0.0.1:3000";
      url+="/imglist";
      this.axios.get(url).then(result=>{
        //2:获取返回结果
        //3:保存data属性中
        console.log(result.data.data);
        this.navlist = result.data.data;
      })
     }
   }
}
</script>
<style>
.app-index .mint-swipe{
    height:375px;
  }
  .app-index .mint-swipe img{
    width:100%;
  }

/**/
  .new-product-box{
    height:250px;
    width:100%;
  }
  .new-title{
    margin-top:10px;
    font-size: 0.37rem;
    color: #3C2314;
    position: relative;
    font-weight: bold;
  }
  .newBoxundefined{ 
    height:117px;
  }
  .newBoxundefined .items{
    padding:0;
    list-style:none;
    display: -webkit-box;
    overflow-x: auto;
    -webkit-overflow-scrolling:touch;
  }
  .newBoxundefined .item{
    display: -webkit-box;
    white-space: nowrap;
    margin-right:10px;
  }
  .item  .new-img{
    width:163px;
    height:117px;
  }
  .item p{
    text-align:center;
  }
  .advertising{
    margin-top:10px;
  }
  .advertising .new-img{
    width:100%
  }
  .slide-box::-webkit-scrollbar { /*隐藏掉滚动条*/
    display: none;
  }
/**/
  .small-img{list-style:none;padding:0;margin:0;}
  .small-img .small-li{float:left;margin-left:19px;margin-top:10px;}
  .small-img .small-li .more{
    padding:0;margin:0;
    width:160px;height:116px;}
  .small-img .small-li p{
  margin:0;
  margin-left:23px;
  font-size:12px;
  color:#3C2314;}
.ioc{
    width:33.75px;
    height:30px;
  }
  .new-more{
    position: absolute;
    right: 0.2rem;
    bottom: 0rem;
    font-weight: normal;
  }
  .new-title{
    margin-top:10px;
    margin-bottom:5px;
  }
</style>