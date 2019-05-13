<template>
  <section class="row">
    <section class="col-md-2">

    <!-- 头导航： 所有、今天、日历-->

      <sidebar :items="headItems"/>

      <div id="tabButtons" class="btn-group btn-group-justified" role="group" aria-label="...">     
        <div v-for="button in tabButtons" :key=button.id class="btn-group" role="group">
          <button type="button" class="btn btn-default" 
              :class="{active: currentTabComponent == button}"
              @click.prevent="changeCurrentTab">
            {{button}}
          </button>
        </div>
      </div>
      
      <keep-alive>
        <component :is="currentTabComponent"></component>
      </keep-alive>
  
    </section>

    <section class="col-md-6">
      <todo-content/>
    </section>
  </section>

</template>

<script>
import sidebar from "./sidebars/sidebar.vue";
import floders from "./sidebars/floders.vue";
import tags from "./sidebars/tags.vue";
import todoContent from "./todo-content/todo-content.vue";

export default {
  name: 'home',
  components: {
    sidebar,
    floders,
    tags,
    todoContent,
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
          icon: "glyphicon glyphicon-fire",
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
      tabButtons: [
        'floders',
        'tags',
      ],
      currentTabIndex: 0,
      currentTab: "floders",
      
    }
  },
  computed: {
    currentTabComponent: function () {
      return this.currentTab;
    },

  },
  methods: {
    changeCurrentTab: function(event){
      let button = event.target.innerText;
      this.currentTab = button;
      
    }
  }
}
</script>

<style scoped="scoped">
@import "https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css";

.sidebar {
  max-width: 100%;
  /*top: -10px;*/
}

</style>
