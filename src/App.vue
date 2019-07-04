<template>
  <div>
      <app-item v-if="!landing"></app-item>

    <div class="landing">
      <div v-if="landing" @click="toggleLanding" class="maxi" :class="{maxihover: show}">
        
      </div>
      <div v-if="landing" @click="toggleLanding" class="willys" @mouseover="toggleShow" @mouseleave="toggleShow" >
        
      </div>
      
    </div>
    
</div>

</template>

<script>
import Diary from './components/Diary.vue'
import Item from './components/Item.vue'
import Bread from './components/Bread.vue'
import Meat from './components/Meat.vue'
import Veggie from './components/Veggie.vue'
export default{
  data(){
    return{
      landing: true,
      show:false,
      showMaxi:true,
      
    }
  },
  components:{
    appItem:Item,
    
  },
  methods:{
    
    toggleShow(){
      this.show = !this.show;
    },
    toggleLanding(){
      this.landing = !this.landing;
    }
    }
  }
  

</script>

<style>

.landing{
  margin-top: 50px;
  display: grid;
  grid-template-columns: 1fr 1% 1fr;
  grid-template-rows: 200px 200px;

}

.maxi{
  text-align: center;
  color: white;
  margin-left: 10%;
background-image:    url('./assets/pics/maxi.gif');
    background-size:     cover;                      /* <------ */
    background-repeat:   no-repeat;
    background-position: center center;  grid-column: 1;
  grid-row: 1;

  
}

.willys{
  border: 2px solid black;
  text-align: center;
  margin-right: 10%;
 background-image:    url('./assets/pics/willys.jpg');
    background-size:     cover;                      /* <------ */
    background-repeat:   no-repeat;
    background-position: center center;  grid-column: 3;
  grid-row: 2;

}

@keyframes landingM {
  from{grid-column:1;}
  to{grid-column: 1/4;}
  
}

.maxi:hover{
  /* margin-right: 10%;
  margin-left: 10%; */
  /* grid-column: 1/4;
  grid-row: 1/3; */
  transition: all .2s ease-in-out;
  transform: scale(1.2);
  background-image:    url('./assets/pics/maxi.gif');
    background-size:     cover;                      /* <------ */
    background-repeat:   no-repeat;
    background-position: center center;
  
}


.willys:hover{
  /* margin-right: 10%;
  margin-left: 10%; */
  /* grid-column: 1/4;
  grid-row: 1/3; */
  transition: all .2s ease-in-out;
  transform: scale(1.2);
   background-image:    url('./assets/pics/willys.jpg');
    background-size:     cover;                      /* <------ */
    background-repeat:   no-repeat;
    background-position: center center;


}

.maxihover{
  transition: all .2s ease-in-out;
  transform: scale(0.7);
}

.maxi:hover ~ .willys{
  transition: all .2s ease-in-out;
  transform: scale(0.7);
}
/* .shopping{
text-align: center;
height: 100vh;


}

  .main{
    display: inline-block;
    width: 70%;    
    grid-template-columns: 1fr;
    list-style: none

  } */
</style>
