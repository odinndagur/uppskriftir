<template>
  <div id="app" class="container">
  <div class="header">
    <h1>{{ title }}</h1>
  </div>

  <div>
    <ul>
      <li v-for="day in menu" :key="day.day" @click="{{day.locked = !day.locked}}"> 
        <div class="day">
        <b style="text-align:left;">{{day.day}}</b> 
        <br/>
        <span style="text-align:right;">{{day.recipe}}
        <span v-if="day.locked">
        🔑
        </span>
        <!--<input type="checkbox" :id="day.day" v-model="day.locked">
        <label :for="day.day"></label>-->
        </span>
        </div>
        </li>
    </ul>
  </div>

  <div class="randombtn" @click="randomMenu">
    Randomize
  </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  mounted() {
    console.log("mounted");
    this.$nextTick(() => {
      // Fires before full page is rendered
    });
  },
  data() {
    return {
      title: "Uppskriftir",
      recipes: [
          "Oumph pasta",
          "Vefjur með like chicken",
          "Pítur",
          "Kaupa mat",
          "Pizza",
          "Tillur",
      ],
      menu: [
        {
          day: "Mánudagur",
          recipe: '',
          locked: false,
        },
        {
          day: "Þriðjudagur",
          recipe: '',
          locked: false,
        },
        {
          day: "Miðvikudagur",
          recipe: '',
          locked: false,
        },
        {
          day: "Fimmtudagur",
          recipe: '',
          locked: false,
        },
        {
          day: "Föstudagur",
          recipe: '',
          locked: false,
        },
        {
          day: "Laugardagur",
          recipe: '',
          locked: false,
        },
        {
          day: "Sunnudagur",
          recipe: 'Húsalind',
          locked: false,
        },
      ],
    };
  },
  methods: {
    randomMenu(){
      this.menu.forEach(day=>{
        if(!day.locked){
        day.recipe = this.recipes[Math.floor(Math.random(1)*this.recipes.length)];
        }
      })
    }
  },
  created: function () {},
};
</script>

<style scoped>
.container {
  display: grid;
  grid-template-columns: 100%;
  grid-template-rows: 40px auto 40px;
}

.day {
  min-height: 2rem;
}

b.date {
text-align: right;
}

span.dayrecipe {
  text-align: right;
}

.item {
  /* border:1px solid black; */
}
/* img {
  display: block;
  margin: auto;
  width: 20rem;
} */

.randombtn{
  background: rgba(100,100,100,100);
  margin:auto;
}

li {
  list-style-type:none;
}

form {
  margin-top: 1rem;
}

input {
  width: 70%;
  height: 2rem;
  margin-top: 0.5rem;
  margin-bottom: 1rem;
}

ul {
  padding-top: 1rem;
  font-size: 1.5rem;
  text-align: left;
}

ul > li:nth-child(even) {
  color: grey;
}

ul button {
  margin: 0 10px;
}

ul a {
  margin: 0 10px;
}

ul a:hover {
  /* display:none; */
}

.header {
  grid-row: 1;
  align-self: top;
}
</style>
