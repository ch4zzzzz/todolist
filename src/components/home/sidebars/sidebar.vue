<template>
  <section class="sidebar">
    <div class="form-group" v-if="addItem">
      <input type="text" class="form-control" id="addInput"
          autocomplete="off"
          :placeholder="addPlaceholder"
          v-model="newItem"
          @keyup.enter.prevent="add">

    </div>
    
    <ul class="list-group">
      <li v-for="item in items" :key="item.id" class="list-group-item">
        <a :href="item.href">
          <span :class="item.icon" aria-hidden="true"></span>
          &nbsp;
          {{item.name}}
        </a>
      </li>
    </ul>

  </section>
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
    defaultIcon: String,
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
      let id;
      if(len>0){
        id = items[len-1]['id']+1
      }
      else{
        id = 0;
      }
      let thisOne = {
        "id": id,
        "name": this.newItem,
        "icon": this.defaultIcon,
        "href": "#",
      }
      this.newItem = "";
      items.push(thisOne);
      //POST
      this.$http.post(this.addRequestUrl, thisOne).then(response => {
        items[len]['href'] = "";
        console.log("post");
      }, response => {
        //error callback
      });

    }
  }
}
</script>

<style scoped="scoped">
@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";

.sidebar {
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

.form-group {
  margin-bottom: 0;
}
</style>
