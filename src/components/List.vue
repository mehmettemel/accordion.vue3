<template>
  <div>
    <ul class="wrapper">
      <li v-for="(item,i) in list" :key="i">
        <i class="fas fa-chevron-circle-right"
            :class="{'open':item.open}"
        ></i>
        <div class="title" @click="item.open = !item.open">
          {{item.title}}
        </div>
        <list-item :list="item"></list-item>
      </li>
    </ul>

  </div>
</template>

<script>
import ListItem from './ListItem.vue';
  export default {
    components:{
      ListItem
    },
     data: () => {
      return {
        /*
          Some test data for the accordion, 
          you can use this for a sidebar navigation or simply as a faq list, for example
        */
        list: [
          {
            title: "Projects",
            open: false,
            sublist: [
              "Vue.js", "SCSS", "JavaScript", "Webpack"
            ]
          },
          {
            title: "Portfolio",
            open: false,
            sublist: [ "Transitions", "Course A" ]
          },
          { 
            title: "Timeline", 
            open: false, 
            sublist: [ "2017", "2018", "2019" ] 
          },
          {
            title: "Resources",
            open: false,
            sublist: ["GitHub", "YouTube", "Dev.to"]
          },
          {
            title: "Documentation",
            open: false,
            sublist: ["Article A", "Article B"]
          }
        ]
      };
    },
  }
</script>

<style lang="scss" scoped>
.wrapper{
  list-style: none;
  background-color: #fefefe;
  box-shadow: 0 2px rgba($color: #463333, $alpha: .15);
  border-radius: 4px;
  overflow: hidden;
  width: 80%;
  li{
    position: relative;
    color: #555;
    border-top: 1px solid #dedede;
    cursor: pointer;

    .title{
      padding: 10px 0;
      text-indent: 20px;
    }

    i{
      position: absolute;
      top: 14px;
      right: 10px;
      transition: all .5s ease;

      &.open{
        transform: rotateZ(90deg);
        color: #463333;
      }
    }

    &:hover{
      color: #fff0f0; 
      background-color: #835858;

    }
  }
}
</style>