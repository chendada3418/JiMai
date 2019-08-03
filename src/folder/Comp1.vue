<template>
  <div class="mybox">
    <span>动画效果</span>
    <br />
    <button @click="add">动画按钮</button>

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
      <li v-for="(item) in arr" :key="item.id">
        {{item.val}}
        <input type="button" @click="add3(item.id)" value="删除"/>
      </li>
    </transition-group>
  </div>
</template>


<script>
export default {
  data() {
    return {
      a: true,
      str: "",
      arr: []
    };
  },
  methods: {
    add() {
      this.a = !this.a;
    },
    add2() {
      this.arr.push({"val":this.str,"id":new Date().getTime()});
      // this.str = "";
      
    },
    add3(id){
      var ind = this.arr.findIndex(obj=>obj.id === id);
      this.arr.splice(ind,1)
      
    }
  }
};
</script>

<style>
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
</style>

