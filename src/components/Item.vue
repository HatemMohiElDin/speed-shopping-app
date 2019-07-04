<template>
<div>
<div class="jumbotron">

  
  <h1>Shopping Rundan</h1>
  <div>
<div class="input-group">
  <!-- <input type="text" 
  class="form-control"
  placeholder="Enter product name" 
  aria-label="Recipient's username" 
  aria-describedby="basic-addon2"
  v-model="userInput" v-on:keyup.enter="addItem"> -->

  <!-- <div class="input-group-append btn-bg-color">
    <button @click="addItem" class="btn btn-outline-secondary" type="button">Add</button>
    <button  @click="sortItems" class="btn btn-outline-secondary" type="button">Sort Items</button>
  </div> -->
  </div>
  <div>
    <ul>
      <li v-for="item in userList" :key="item.id"> {{item}} </li>
    </ul>
  </div>
  <hr>
  <button @click="sortItems"></button>
</div>


    <!-- <input v-model="userInput" v-on:keyup.enter="addItem" type="text">  
    <button  @click="addItem">Add</button>
    <ul>
      <li v-for="item in userList" :key="item.id"> {{item}} </li>
    </ul>

  <button @click="sortItems">Sort Items</button>
  <hr>
  </div> -->
    <div>

  <app-veggie :userVeggie="userVeggie">  </app-veggie>
  <app-bread :userBread="userBread"></app-bread>
  <app-diary :userDiary="userDiary"></app-diary>
  <app-meat :userMeat="userMeat"></app-meat>
  <app-frozen :userFrozen="userFrozen"></app-frozen>
 </div>

</div>
</div>
</template>

<script>
import Veggie from './Veggie.vue'
import Meat from './Meat.vue'
import Diary from './Diary.vue'
import Bread from './Bread.vue'
import Frozen from './Frozen.vue'
import Counter from './Counter.vue'

export default {
  data(){
    return{
      userInput: "",
      userList:[],
      diaryItems:['mjölk','yogurt','ägg','grädde','creme fresh','filmjölk','gräddfil'],
      veggieItems:['tomat','gurka','sallad','morot','champinjon','lök',
      'vitlök','citron','paprika','blomkol','äpple','päron','vattenmelon','vindruvor',
      'apelsin','mandarin','poptatis','broccoli','palsternacka','avocado'],
      meatItems:['lövbiff', 'köttfärs', 'högrev','francyska','hel kyckling'],
      breadItems:['toast','korvbröd','hamburgarbröd','frallor','kanelbullar'],
      frozenItems:['kyckling','libabröd','hamburgare','pommes','wok','ärtor','fasolya'],
      colonialItems:['ris','pasta','flingor','musli','smörgåsgurka','hommos'],
      cheeseItems:['prästost','herrgård','västerbotten','philadelphia','gouda','riven ost','mozarella',
      'mögelost'],
      polaggItems:['kalkon','saltrulle','korv','rostbiff',''],
      drinksItems:['kaffe','te','cider','cola'],
      hygieneItems:['tvål','tandkräm','qtips','deoderant'],
      babyItems:['blöjor','wipes','semper'],
      worldfoodItems:['kryddor','olja','soppa','vinäger','bernaisesås','hollandaisesås','currysås','soyasås',
      'chilisås','bbqsås','tortilla','fefferoni'],
      userDiary:[],
      userVeggie:[],
      userMeat:[],
      userBread:[],
      userFrozen:[],
      userColonial:[],
      userCheese:[],
      userPolagg:[],
      userDrinks:[],
      userHygiene:[],
      userBaby:[],
      userWorldfood:[]

    }
  },
  components:{
    appVeggie:Veggie,
    appMeat:Meat,
    appDiary:Diary,
    appBread:Bread,
    appFrozen:Frozen,
    appCounter:Counter,

  },
  methods:{
    addItem(){
      this.userList.push(this.userInput);
      this.userInput=""      
    },
    // sortItems(){
    //   this.$emit('itemarray', this.userList); 
    //   this.userList=[]

    // },

    sortItems(){
      this.userList.forEach((item) => {
        if(this.diaryItems.includes(item)){
          this.userDiary.push(item)        
        } else if(this.veggieItems.includes(item)){
          this.userVeggie.push(item)
        }else if(this.meatItems.includes(item)){
          this.userMeat.push(item)
        }else if(this.breadItems.includes(item)){
          this.userBread.push(item)
        } else if(this.frozenItems.includes(item)){
          this.userFrozen.push(item)
        }else {
          alert(`${item} is not part of my vocabulary`)
        }
       })
      this.userList=[]
  }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
@import '../assets/styles/products.css';

li{
  list-style: none
}
   
</style>
