
<template>
  <div id="app">
     <div v-if="list.length">
        <table>
          <thead>
            <tr>
              <th></th>
              <th>商品名称</th>
              <th>商品单价</th>
              <th>商品数量</th>
              <th></th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(item,index) in list">
              <td>{{index+1}}</td>
              <td>{{item.name}}</td>
              <td>{{item.price}}</td>
              <td>
                <button
                  @click="handleReduce(index)"
                  :disabled="item.count === 1">-</button>
                {{item.count}}
                <button @click="handleAdd(index)">+</button>
              </td>
              <td>
                <button @click="handleRemove(index)">移除</button>
              </td>
            </tr>
          </tbody>
        </table>
       </div>
        <div>总价：RMB{{ totalPrice }}</div>
    <router-view/>
    </div>
</template>

<script>
export default {
  name: 'app',
  data:function(){
    return {
      list:[
      {
        id:1,
        name:"iphone7",
        price:"6188",
        count:1
      },
       {
        id:1,
        name:"iPad Pro",
        price:"5888",
        count:1
      },
       {
        id:3,
        name:"Macbook Pro",
        price:"21488",
        count:1
      }  
     ]
    }
  },
  computed:{
    totalPrice:function(){
      var total = 0;
      for(var i = 0 ; i < this.list.length; i++){
        var item = this.list[i];
        total += item.price * item.count;
      }
      return total.toString().replace(/\B(?=(\d{3})+$)/g,",");
    }
  },
  methods:{
    handleReduce:function(index){
      if(this.list[index].count === 1) return;
      this.list[index].count--;
    },
    handleAdd:function(index){
      this.list[index].count++;
    },
    handleRemove:function(index){
      this.list.splice(index,1);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
[v-cloak]{
  display: none;
}
table{
  border:1px solid #e9e9e9;
  border-collapse: collapse;
  border-spacing: 0;
  empty-cells: show;
}
th,td{
  padding: 8px 16px;
  border: 1px solid #e9e9e9;
  text-align: left；
}
th{
  background: #f7f7f7;
  color:#5c6b77;
  font-weight: 600;
  white-space: nowrap;
  }
</style>
