<template>
  <div class="content-box">
    <div class="my_info">
      <div class="info_left">
        <div class="info_img">
          <img :src="user.headimgurl" alt />
        </div>
        <div class="info_name">
          <span v-text="user.nickname"></span>
          <mt-badge size="small" color="red">未购券</mt-badge>
        </div>
      </div>
    </div>
    <div class="my_nav_wrap">
      <div class="my_nav">
        <div class="nav_bar">
          <div class="bar_item" @click="go">
            <div class="bar_title">已浏览数</div>
            <div class="bar_num">0</div>
          </div>
          <div class="bar_item" @click="go">
            <div class="bar_title">已售券数</div>
            <div class="bar_num">0</div>
          </div>
          <div class="bar_item" @click="go">
            <div class="bar_title">我的奖励</div>
            <div class="bar_num">
              <span>18元</span>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="my_app_list">
      <router-link class="item" :to="{path: '/'}">
        <div class="left">
          <img src="../../assets/imgs/order.jpg" alt />
          我的订单
        </div>
        <div class="right">></div>
      </router-link>
   <router-link class="item" :to="{path: '/'}">
        <div class="left">
          <img src="../../assets/imgs/coupon.jpg" alt />
          优惠券
        </div>
        <div class="right">></div>
      </router-link>
         <router-link class="item" :to="{path: '/'}">
        <div class="left">
          <img src="../../assets/imgs/partener.jpg" alt />
         申请合作
        </div>
        <div class="right">></div>
      </router-link>
    </div>

    <div class="page-content">
      <mt-button @click="todetail">user</mt-button>
    </div>
  </div>
</template>

<script>
import { mapMutations, mapGetters, mapState } from "vuex";
export default {
  data() {
    return {
      tittle: "激情燃烧的岁月",
      num: 0,
      user: this.$store.state.my.ueserInfo
    };
  },
  created() {
    console.log(this.$store.state.my.ueserInfo);
  },
  methods: {
    ...mapMutations({
      setNum: "SET_NUM"
    }),
    todetail() {
      this.$router.togo("/Home/Detail");
    },
    handleLink(url) {
      this.$router.togo(url);
    }
  },
  computed: {
    ...mapGetters(["number"]),
    ...mapState({
      number: state => state.home.number
    })
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
@import "~styles/index.less";
@import "~styles/variable.less";
.page-content {
  .mb(98);
}
.my_info {
  padding: 40px;
  border: 1px solid #ccc;
  .info_left {
    display: flex;
    align-items: center;
    .info_img {
      width: 60px;
      height: 60px;
      border: 1px solid #ccc;
      border-radius: 50%;
      margin-right: 10px;
      img {
        width: 100%;
        height: 100%;
      }
    }
    .info_name {
      display: flex;
      height: 60px;
      flex-direction: column;
      justify-content: space-around;
    }
  }
}
.my_nav_wrap {
  .my_nav {
    padding: 10px;
    border: 1px solid red;
    .nav_bar {
      display: flex;
      .bar_item {
        flex: 1;
        span {
          color: red;
        }
      }
    }
  }
}
.my_app_list {
  text-align: left;
  font-size:16px;
  .item{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding:10px 15px;
    margin-bottom:10px;
    border-bottom:1px solid #ccc;
    .left{
      display: flex;
      align-items: center;
      img{
        width: 20px;
        height: 20px;
        margin-right:10px;
      }
    }
  }
}
</style>
