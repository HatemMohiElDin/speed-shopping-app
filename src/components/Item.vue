<template>
  <div>
    <div class="container">
      <div class="jumbotron">
        <h1>Shopping Rundan</h1>
        <div class="topper">
          <div class="input-group">
            <input
              type="text"
              class="form-control"
              placeholder="Enter product name"
              aria-label="Recipient's username"
              aria-describedby="basic-addon2"
              v-model="userInput"
              v-on:keyup.enter="addItem"
            />

            <button @click="addItem" class="btn btn-outline-secondary btn-sm" type="button">Add</button>
            <button
              @click="sortItems"
              class="btn btn-outline-secondary btn-sm"
              type="button"
            >Sort Items</button>
          </div>
          <div>
            <ul>
              <li v-for="item in userList" :key="item.id">{{item}}</li>
            </ul>
          </div>
          <hr />
        </div>

        <!-- <input v-model="userInput" v-on:keyup.enter="addItem" type="text">  
    <button  @click="addItem">Add</button>
    <ul>
      <li v-for="item in userList" :key="item.id"> {{item}} </li>
    </ul>

  <button @click="sortItems">Sort Items</button>
  <hr>
        </div>-->
        <div>
          <app-veggie :userVeggie="userVeggie">
            <div slot="veggie">
              <h3>Veggies and Fruit</h3>
              <div v-for="(item, index) in userVeggie" :key="item.id">
                <li>
                  {{item}}
                  <i @click="removeItem(userVeggie, index)" class="fa fa-check"></i>
                </li>
              </div>
            </div>
          </app-veggie>
          <app-bread :userBread="userBread"></app-bread>
          <app-diary :userDiary="userDiary"></app-diary>
          <app-meat :userMeat="userMeat"></app-meat>
          <app-frozen :userFrozen="userFrozen"></app-frozen>
          <div>
            <h2>Other</h2>
            <li v-for="item in userOther" :key="item.id">{{item}}</li>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Veggie from "./Veggie.vue";
import Meat from "./Meat.vue";
import Diary from "./Diary.vue";
import Bread from "./Bread.vue";
import Frozen from "./Frozen.vue";

export default {
  data() {
    return {
      userInput: "",
      userList: [],
      diaryItems: [
        "mjölk",
        "yogurt",
        "ägg",
        "grädde",
        "creme fresh",
        "filmjölk",
        "gräddfil"
      ],
      veggieItems: [
        "tomat",
        "gurka",
        "sallad",
        "morot",
        "champinjon",
        "lök",
        "vitlök",
        "citron",
        "paprika",
        "blomkol",
        "äpple",
        "päron",
        "vattenmelon",
        "vindruvor",
        "apelsin",
        "mandarin",
        "poptatis",
        "broccoli",
        "palsternacka",
        "avocado"
      ],
      meatItems: ["lövbiff", "köttfärs", "högrev", "francyska", "hel kyckling"],
      breadItems: [
        "toast",
        "korvbröd",
        "hamburgarbröd",
        "frallor",
        "kanelbullar"
      ],
      frozenItems: [
        "kyckling",
        "libabröd",
        "hamburgare",
        "pommes",
        "wok",
        "ärtor",
        "fasolya"
      ],
      colonialItems: [
        "ris",
        "pasta",
        "flingor",
        "musli",
        "smörgåsgurka",
        "hommos"
      ],
      cheeseItems: [
        "prästost",
        "herrgård",
        "västerbotten",
        "philadelphia",
        "gouda",
        "riven ost",
        "mozarella",
        "mögelost"
      ],
      polaggItems: ["kalkon", "saltrulle", "korv", "rostbiff", ""],
      drinksItems: ["kaffe", "te", "cider", "cola"],
      hygieneItems: ["tvål", "tandkräm", "qtips", "deoderant"],
      babyItems: ["blöjor", "wipes", "semper"],
      worldfoodItems: [
        "kryddor",
        "olja",
        "soppa",
        "vinäger",
        "bernaisesås",
        "hollandaisesås",
        "currysås",
        "soyasås",
        "chilisås",
        "bbqsås",
        "tortilla",
        "fefferoni"
      ],
      userDiary: [],
      userVeggie: [],
      userMeat: [],
      userBread: [],
      userFrozen: [],
      userColonial: [],
      userCheese: [],
      userPolagg: [],
      userDrinks: [],
      userHygiene: [],
      userBaby: [],
      userWorldfood: [],
      userOther: []
    };
  },
  components: {
    appVeggie: Veggie,
    appMeat: Meat,
    appDiary: Diary,
    appBread: Bread,
    appFrozen: Frozen
  },
  methods: {
    addItem() {
      this.userList.push(this.userInput);
      this.userInput = "";
    },
    // sortItems(){
    //   this.$emit('itemarray', this.userList);
    //   this.userList=[]

    // },

    sortItems() {
      this.userList.forEach(item => {
        if (this.diaryItems.includes(item)) {
          this.userDiary.push(item);
        } else if (this.veggieItems.includes(item)) {
          this.userVeggie.push(item);
        } else if (this.meatItems.includes(item)) {
          this.userMeat.push(item);
        } else if (this.breadItems.includes(item)) {
          this.userBread.push(item);
        } else if (this.frozenItems.includes(item)) {
          this.userFrozen.push(item);
        } else {
          alert(`${item} added to Other`);
          this.userOther.push(item);
        }
      });
      this.userList = [];
    },

    removeItem(index) {
      this.userVeggie.splice(index, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
body {
  background: rgba(231, 112, 112, 0.548);
}
.jumbotron {
  max-width: 600px;
  margin: 30px auto;
  padding-top: 5px;
  border: 1px solid red;
  background-image: linear-gradient(120deg, rgb(216, 32, 32), white);

  color: white;
}

h1 {
  width: 100%;
  padding-bottom: 10px;
  margin: 0;
}

.form-control {
  padding: 0;
  margin: 0;
}

li {
  list-style: none;
}
</style>
