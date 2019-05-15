<template>
  <section class="todo-items">
    <section class="unfinished">
      <h4>未完成的</h4>
      <ul>
        <li v-for="item in items" v-if="!item.checked" :key=item.id> 
          <label>
            <input type="checkbox" v-model="item.checked"> {{item.content}}
          </label>
          <button @click="deleteItem(item)">x</button>
        </li>
      </ul>
    </section>
    
    <section class="finished" v-if="showFinished">
      <h4>已完成的</h4>
      <ul>
        <li v-for="item in items" v-if="item.checked" :key=item.id>
          <label>
            <input type="checkbox" v-model="item.checked"> {{item.content}}
          </label>
          <button @click="deleteItem(item)">x</button>
        </li>
      </ul>
    </section>
  </section>
</template>

<script>
export default {
  name: 'todo-items',
  props: {
    items: Array,
    showFinished: Boolean,
  },
  created() {
    this.thisId = this.items.length;
  },
  data(){
    return{
      thisId: 0,
    }
  },
  methods: {
    addItem(content){
      let len = this.items.length;
      let newItem = {
        content,
        id: this.thisId++,
        checked: false,
      };
      this.items.unshift(newItem);
    },
    deleteItem(item){
      let items = this.items;
      items.splice(items.indexOf(item), 1);
    },
  }
}
</script>

<style></style>