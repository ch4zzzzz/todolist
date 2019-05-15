<template>
  <section>

    <h2>{{listName}}</h2>
    <div class="form-group row">
      <div class="col-sm-6 todo-content">
        <input type="text" class="form-control" id="addInput"
          autocomplete="off"
          :placeholder="addPlaceholder"
          v-model="newTodo"
          @keyup.enter.prevent="add">
      </div>
      
      <div class="col-sm-1 date">
        <datepicker v-model="date" name="datepicker"
        class="datepicker"
        ref="datepicker"/>
      </div>
    </div>

    
    
    
  </section>  
</template>


<script>
import Datepicker from 'vuejs-datepicker';

export default {
  name: "todo-content",
  components: {
    Datepicker,

  },
  data: function(){
    return{
      newTodo: "",
      date: "",
      dateFormat: "d",
    }
  },
  props: {
    listName: {
      type: String,
      default: "添加任务",
    },
    addPlaceholder: {
      type: String,
      default: "添加任务",
    },
  },
  methods: {
    

  }

}
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";


.datepicker input {
  width: 35px;   
  height: 35px;   
  background: url("./calendar-alt.png") no-repeat center;
  background-size: 100% 100%;
  cursor: pointer;
  display: block;   
  font-size: 0;   
  line-height: 0;   
  text-indent: -9999px;
  border: none;
  outline: none;
}

.date {
  display: block;
  float: right;
}

</style>