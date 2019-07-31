<template>
  <div class="hello">
    <mt-tabbar v-model="selected">
      <mt-tab-item id="sibox">
        <img
          slot="icon"
          src="http://game.gtimg.cn/images/gwgo/zlkdatasys/images/image/20190327/c172fd03e8de6781a8cd43bc3aa82566.png"
        />
        圈子公告
      </mt-tab-item>
      <mt-tab-item id="yibox">
        <img
          slot="icon"
          src="http://game.gtimg.cn/images/gwgo/zlkdatasys/images/image/20190327/4ee6acc0e46da4f4f4086ce560cd0a11.png"
        />
        游戏战力
      </mt-tab-item>
      <mt-tab-item id="erbox">
        <img
          slot="icon"
          src="http://game.gtimg.cn/images/gwgo/zlkdatasys/images/image/20190327/8103891085f949fad009641eefc589e0.png"
        />
        游戏经验
      </mt-tab-item>
      <mt-tab-item id="sanbox">
        <img
          slot="icon"
          src="http://game.gtimg.cn/images/gwgo/zlkdatasys/images/image/20190327/77af7ac09e25eb3264618de50091617a.png"
        />
        本周增加
      </mt-tab-item>
    </mt-tabbar>
    <div v-if="selected == 'yibox'" class="powerBox">
      <div>
        <table border="1" cellspacing="0">
          <tr>
            <td>游戏昵称</td>
            <td>游戏等级</td>
            <td>战力</td>
          </tr>
          <tr v-for="(item,index) in listAddf3" :key="index">
            <td>{{item.游戏昵称}}</td>
            <td>{{item.游戏等级}}级</td>
            <td>{{item.游戏战力}}</td>
          </tr>
        </table>
      </div>
    </div>
    <div v-if="selected == 'erbox'" class="powerBox">
      <div>
        <table border="1" cellspacing="0">
          <tr>
            <td>游戏昵称</td>
            <td>游戏等级</td>
            <td>游戏经验</td>
          </tr>
          <tr v-for="(item,index) in listAddf2" :key="index">
            <td>{{item.游戏昵称}}</td>
            <td>{{item.游戏等级}}级</td>
            <td>{{item.游戏经验}}</td>
          </tr>
        </table>
      </div>
    </div>
    <div v-if="selected == 'sanbox'" class="powerBox">
      <div>
        <table border="1" cellspacing="0">
          <tr>
            <td>游戏昵称</td>
            <td>本周增加战力</td>
            <td>本周增加经验</td>
          </tr>
          <tr v-for="(item,index) in listAddf" :key="index">
            <td>{{item.游戏昵称}}</td>
            <td>{{item.增加战力}}</td>
            <td>{{item.增加经验}}</td>
          </tr>
        </table>
      </div>
    </div>
    <div v-if="selected == 'sibox'" class="powerBox">
      <div class="addbox">
        <img src="@/assets/1.png" alt />
        <img src="@/assets/2.png" alt />
        <img src="@/assets/3.png" alt />
        <img src="@/assets/4.png" alt />
        <img src="@/assets/5.png" alt />
      </div>
    </div>
    <div style="height:50px;"></div>
  </div>
</template>

<script>
import str from "@/assets/data.js";
import { Tabbar, TabItem } from "mint-ui";
import { Loadmore } from "mint-ui";
import { Popup } from "mint-ui";
export default {
  name: "HelloWorld",
  components: {
    // TabItem.name: TabItem,
    Tabbar,
    Popup,
    Loadmore,
    TabItem
  },
  data() {
    return {
      msg: str,
      popupVisible: true,
      selected: "sibox",
      listPower: [],
      listexpre: [],
      listAdd: []
    };
  },
  computed: {
    people: function() {
      return JSON.parse(this.msg);
    },
    listAddf: function() {
      var arr = JSON.parse(this.msg);
      var list3 = [];
      for (let i = 0; i < arr.length; i++) {
        list3.push(arr[i]);
      }
      list3.sort(function(x, y) {
        return y["增加经验"] - x["增加经验"];
      });
      console.log(list3);
      return list3;
    },
    listAddf2: function() {
      var arr = JSON.parse(this.msg);
      var list3 = [];
      for (let i = 0; i < arr.length; i++) {
        list3.push(arr[i]);
      }
      list3.sort(function(x, y) {
        return y["游戏等级"] - x["游戏等级"];
      });
      console.log(list3);
      return list3;
    },
    listAddf3: function() {
      var arr = JSON.parse(this.msg);
      var list3 = [];
      for (let i = 0; i < arr.length; i++) {
        list3.push(arr[i]);
      }
      list3.sort(function(x, y) {
        return y["游戏战力"] - x["游戏战力"];
      });
      console.log(list3);
      return list3;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

table{width:100%;text-align:center;border-collapse:collapse;border-spacing:1;border-spacing:0;}


table td{
  word-break: break-all;
  word-wrap:break-word;
}
h1,
h2 {
  font-weight: normal;
}
.addbox img{
  width: 100%;
  margin-top: -4px;
}
img {
  margin: 0;
  padding: 0;

}
.
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.mint-tab-item-label {
  font-size: 14px;
}
.mint-tab-item-icon img {
  width: 27px;
  height: 27px;
}
.powercon {
  border: 1px solid #ccc;
}
.mint-tabbar {
  position: fixed;
  bottom: 0;
}
.powerBox table {
  width: 100%;
}
.powerBox table tr td:nth-child(1) {
  width: 40%;
}
.powerBox table tr:nth-child(1) {
  background: rgb(87,138,61);;
  color: #fff;
  font-weight: bold;
}


.powerBox table tr:nth-child(2n) {
  background: #d7d7d7;
}
.powerBox table tr:hover{
  background:rgb(171,185,97);;
}

</style>
