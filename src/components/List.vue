<template>
  <!-- for文でlocalstrageを出力 -->
  <div class="list">
    <div class="listheader">
      <p class="list-title">{{ title }}</p>
      <div class="deletelist" @click="removeList">
        X
      </div>
    </div>
    <Card v-for="(item,index) in cards"
      :key="item.id"
      :body="item.body"
      :listIndex="listIndex"
      :cardIndex="index"
    />
    <card-add :listIndex="listIndex" />
  </div>
</template>

<script>
import CardAdd from './CardAdd'
import Card from './Card'
export default {
  components: {
    CardAdd,
    Card,
  },
  props: {
    title: {
      type:String,
      required:true
    },
    cards: {
      type: Array,
      required: true
    },
    listIndex: {
      type:Number,
      required:true
    }
  },
  methods:{
    removeList:function(){
      if(confirm("本当にこのリストを削除しますか？")){
        this.$store.dispatch('removelist',{listIndex: this.listIndex})
      }
    },
  },
}
</script>

<style>
</style>
