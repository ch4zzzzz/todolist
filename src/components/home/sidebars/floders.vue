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
  name: "floders",
  components: {
    sidebar,
  },
  data: function(){
    return{
      items: [],
      addItem: true,
      postURL: "",
      addRequestUrl: "",
      icon: "glyphicon glyphicon-list",
    }
  },
  created: function(){
    console.log("created floders.vue");
    this.$http.post(this.postURL).then(response => {

    }, response => {

    });
  },
}
</script>

<style>

</style>
