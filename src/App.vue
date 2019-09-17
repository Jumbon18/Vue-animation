<template>
  <div class="container text-center pt-5">
    <button class="btn btn-success" @click="add">Add</button>
    <button class="btn btn-danger" @click="remove">Remove</button>
    <hr>
    <transition-group tag="ul" class="list-group width300" name="ma">

      <li class="list-group-item" v-for="(item,i) of items" :key="i">{{item}}</li>
    </transition-group>
  </div>
</template>

<script>

export default {
  name: 'app',
  data:()=>({
      items:[1,2,3,4,5],
    nextNum:6
  }),
  methods:{
    add(){
      this.items.splice(this.getIndex(),0,this.nextNum++)
    },
    remove(){
      this.items.splice(this.getIndex(),1);
    },
    getIndex(){
      return Math.floor(Math.random() * this.items.length)
    }
  }
}
</script>

<style>
.width300{
  width: 300px;
  margin: 0 auto;
}
  .ma-enter-active,.ma-leave-active{
    transition: 1s all;
  }
  .ma-enter,.ma-leave-to{
    transform: translateX(-100px);
  }
.ma-leave{
  opacity:1 ;
}
  .ma-leave-to{
    opacity: 0;
  }
</style>
