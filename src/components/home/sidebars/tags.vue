<template>
  <sidebar
    :items="items" 
    :addItem="addItem"
    :addRequestUrl="addRequestUrl"
    :defaultIcon="icon"
    />
</template>

<script>
import sidebar from "./sidebar.vue";

export default {
  name: "tags",
  components: {
    sidebar,
  },
  data: function(){
    return{
      items: [],
      addItem: true,
      postURL: "",
      addRequestUrl: "", 
      icon: "glyphicon glyphicon-tag",
    }
  },
  created: function(){
    console.log("created tags.vue");
    this.$http.post(this.postURL).then(response => {

    }, response => {

    });
  },

}
</script>

<style>

</style>
