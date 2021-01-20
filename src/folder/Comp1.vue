<template>
  <div class="mybox">
    <span>动画效果</span>
    <span>测试更新</span>
    <br />
    <button @click="add">动画按钮</button>
    <button @click="fn3('哈哈哈')">对话框</button>

    <transition
      enter-class
      enter-active-class="animated fadeInLeft"
      enter-to-class
      leave-class
      leave-active-class="animated fadeOutLeft"
      leave-to-class
    >
      <div class="mydiv" v-if="a">
        <ul>
          <li>1</li>
          <li>2</li>
          <li>3</li>
          <li>4</li>
        </ul>
      </div>
    </transition>
    <input type="text" v-model="str" />
    <button @click="add2">添加</button>
    <transition-group
      enter-class
      enter-active-class="animated bounceInDown"
      enter-to-class
      leave-class
      leave-active-class="animated fadeOutLeft"
      leave-to-class
    >
      <li v-for="item in arr" :key="item.id">
        {{ item.val }}
        <input type="button" @click="add3(item.id,item.val)" value="删除" />
      </li>
    </transition-group>

    <transition
      enter-class
      enter-active-class="animated fadeIn"
      enter-to-class
      leave-class
      leave-active-class="animated fadeOut"
      leave-to-class
    >
      <div class="toast" v-if="msg">{{ msgText }}</div>
    </transition>
  </div>
</template>


<script>
export default {
  data() {
    return {
      a: true,
      str: "",
      arr: [],
      msg: false,
      msgText: "默认的数据",
    };
  },
  methods: {
    add() {
      this.a = !this.a;
    },
    add2() {
      if (this.str == "") {
        alert("请输入要添加的内容");
      } else {
        this.arr.push({ val: this.str, id: new Date().getTime() });
        this.str = "";
        console.log({ id: new Date().getTime() });
      }
    },
    add3(id,val) {
      // var ind = this.arr.findIndex(obj=>obj.id === id);
      var ind = this.arr.findIndex((obj) => {
        return obj.id === id;
      });

      this.arr.splice(ind, 1);
      console.log(val,id);
    },
    fn3(tit) {
      this.msg = true;
      this.msgText = tit;
      setTimeout(() => {
        this.msg = false;
      }, 1500);
    },
  },
};
</script>

<style>
/* 引入文件方式 */
/* @import url(https://cdn.bootcss.com/animate.css/3.7.0/animate.min.css); */
.mybox {
  margin: 0;
  padding: 0;
  background: gray;
}
button {
  display: inline-block;
  border: 1px solid red;
}
.mydiv {
  position: fixed;
  width: 200px;
  height: 450px;
  border: 1px solid gray;
  background: pink;
}
.toast {
  transform: translate(-50%, -50%);
  position: fixed;
  left: 50%;
  top: 50%;
  color: white;
  border-radius: 5px;
  padding: 8px;
  background: rgba(0, 0, 0, 0.6);
}
</style>

