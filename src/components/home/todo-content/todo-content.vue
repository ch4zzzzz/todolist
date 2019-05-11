<template>
  <section>
    <h2>{{listName}}</h2>
    <div class="form-group">
      <input type="text" class="form-control" id="addInput"
          autocomplete="off"
          :placeholder="addPlaceholder"
          v-model="newTodo"
          @keyup.enter.prevent="add">

    </div>
  </section>  
</template>

<script>
export default {
  name: "todo-content",
  data: function(){
    return{
      newTodo: "",
    }
  },
  props: {
    listName: String,
    addPlaceholder: {
      type: String,
      default: "添加任务"
    }
  },

}
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";

</style>