<template>
  <nav>
    <ul class="list-group">
      <li v-for="item in items" :key="item.id" class="list-group-item">
        <a :href="item.href">
          <span :class="item.icon" aria-hidden="true"></span>
          &nbsp;
          {{item.name}}
        </a>
      </li>
      <!-- <li class="list-group-item" v-if="addItem">
        <a href="#" v-on:click.prevent="add">
          <span class="glyphicon glyphicon-plus" aria-hidden="true"></span>
          &nbsp;
          添加
        </a>
      </li> -->

      <div class="form-group" v-if="addItem">
        <input type="text" class="form-control" id="addInput"
            autocomplete="off"
            :placeholder="addPlaceholder"
            v-model="newItem"
            @keyup.enter.prevent="add">
      </div>


    </ul>
  </nav>
</template>

<script>
import "vue-resource";

export default {
  name: 'sidebar',
  components: {

  },
  data: function(){
    return{
      newItem: "",
    }
  },
  props: {
    items: Array,
    icon: String,
    addItem: Boolean,
    addPlaceholder: {
      type: String,
      default: "Add an item",
    },
    addRequestUrl: String,
  },
  computed: {

  },
  methods: {
    add: function(){
      let items = this.items;
      let len = items.length;
      let id = items[len-1]['id']+1;
      let thisOne = {
        "id": id,
        "name": this.newItem,
        "href": "#",
      }
      items.push(thisOne);

      //POST
      this.$http.post(addRequestUrl, thisOne).then(response => {
        console.log("post");
      }, response => {
        //error callback
      });


    }
  }
}
</script>

<style scoped="scoped">
nav {
  max-width: 200px;
}

li {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: "…";
  width: auto;
}

li a {
  color: black;
  text-decoration: none;
  display: block;
  width: 100%;
}

li a :hover{

}


@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";
</style>
