<template>
  <section class="row">

    <!-- 头导航： 所有、今天、日历-->
    <sidebar class="sidebar col-md-3"
      :items="headItems"
    />


    <component :is="currentTabComponent"></component>
  </section>
</template>

<script>
import sidebar from "./sidebars/sidebar.vue";
import floders from "./sidebars/floders.vue";
import tags from "./sidebars/tags.vue";

export default {
  name: 'home',
  components: {
    sidebar,
    floders,
    tags,
  },
  data: function(){
    return{
      icon: "glyphicon glyphicon-th-list",
      headItems: [
        {
          id: 1,
          name: "所有",
          href: "#",
          icon: "glyphicon glyphicon-folder-close",
        },
        {
          id: 2,
          name: "今天",
          href: "#",
          icon: "",
        },
        {
          id: 3,
          name: "日历",
          href: "#",
          icon: "glyphicon glyphicon-calendar",
        },
        {
          id: 4,
          name: "收集箱",
          href: "#",
          icon: "glyphicon glyphicon-list-alt",
        },
      ],
      addPlaceholder: "添加",
      currentTab: "tags",
    }
  },
  computed: {
    currentTabComponent: function () {
      return this.currentTab;
    }
  }

}
</script>

<style scoped="scoped">
.sidebar {
  max-width: 200px;
}
</style>
