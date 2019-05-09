<template>
  <sidebar
    :items="items"
    :addItem="true"
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
      items: [
        {
          id: 1,
          name: "1",
          href: "#",
          icon: "glyphicon glyphicon-th-list",
        },
      ]


    }
  },

}
</script>

<style>

</style>
