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

        <div>
          <div class="hygiene">
            <h3>Hygiene</h3>
            <div v-for="(item, index) in userHygiene" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userHygiene)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="baby">
            <h3>Baby stuff</h3>
            <div v-for="(item, index) in userBaby" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userBaby)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Colonial">
            <h3>Colonial</h3>
            <div v-for="(item, index) in userColonial" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userColonial)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Worldfood">
            <h3>World food and Spices</h3>
            <div v-for="(item, index) in userWorldfood" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userWorldfood)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="veggie">
            <h3>Veggies and Fruit</h3>
            <div v-for="(item, index) in userVeggie" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userVeggie)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Bread">
            <h3>Bread</h3>
            <div v-for="(item, index) in userBread" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userBread)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Diary">
            <h3>Diary</h3>
            <div v-for="(item, index) in userDiary" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userDiary)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Cheese">
            <h3>Cheese</h3>
            <div v-for="(item, index) in userCheese" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userCheese)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Meat">
            <h3>Meats</h3>
            <div v-for="(item, index) in userMeat" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userMeat)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Polagg">
            <h3>Pålägg</h3>
            <div v-for="(item, index) in userPolagg" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userPolagg)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Drinks">
            <h3>Drinks</h3>
            <div v-for="(item, index) in userDrinks" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userDrinks)" class="fa fa-check"></i>
              </li>
            </div>
          </div>
          <div class="Frozen">
            <h3>Frozen</h3>
            <div v-for="(item, index) in userFrozen" :key="item.id">
              <li>
                {{item}}
                <i @click="removeItem(index, userFrozen)" class="fa fa-check"></i>
              </li>
            </div>
          </div>

          <div>
            <h3>Other</h3>
            <li v-for="(item, index) in userOther" :key="item.id">
              {{item}}
              <i @click="removeItem(index, userOther)" class="fa fa-check"></i>
            </li>
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
        "gräddfil",
        "yoggi"
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
        item = item.toLowerCase()
        if (this.diaryItems.includes(item)) {
          this.userDiary.push(item);
        } else if (this.veggieItems.includes(item)) {
          this.userVeggie.push(item);
        } else if (this.meatItems.includes(item)) {
          this.userMeat.push(item);
        } else if (this.breadItems.includes(item)) {
          this.userBread.push(item);
        } else if (this.babyItems.includes(item)) {
          this.userBaby.push(item);
        } else if (this.hygieneItems.includes(item)) {
          this.userHygiene.push(item);
        } else if (this.cheeseItems.includes(item)) {
          this.userCheese.push(item);
        } else if (this.colonialItems.includes(item)) {
          this.userColonial.push(item);
        } else if (this.drinksItems.includes(item)) {
          this.userDrinks.push(item);
        } else if (this.frozenItems.includes(item)) {
          this.userFrozen.push(item);
        } else if (this.polaggItems.includes(item)) {
          this.userPolagg.push(item);
        } else if (this.worldfoodItems.includes(item)) {
          this.userWorldfood.push(item);
        } else {
          alert(`${item} added to Other`);
          this.userOther.push(item);
        }
      });
      this.userList = [];
    },

    removeItem: (index, name) => {
      name.splice(index, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
