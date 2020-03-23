<template>
  <div class="hello">    
    <div>
      <div class="wrap">
        <div class="search">
            <input type="text" class="searchTerm" placeholder="Which extention are you looking for?">
            <button type="submit" class="searchButton">
              <i class="fa fa-search"></i>
          </button>
        </div>
      </div>
      <ul v-for="(set, index) in cards" :key="index">
          <b>{{index}}</b>      
          <li v-for="card in set" :key="card.cardId">Card : {{card.name}}; Effect : {{card.text}}</li>        
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HearthStoneCards',
  created() {
    this.getAll();
  },
  computed: {
    cards() {
      return this.$store.getters.getCards;
    },
  },
  methods: {
    getAll() {      
      const config = {
          headers: {
            "x-rapidapi-host": "omgvamp-hearthstone-v1.p.rapidapi.com",
            "x-rapidapi-key": "8f63c7eeddmsh9c1c7a90ad44690p1ae244jsn86d02298a4b9"
          }
      };
      axios.get('https://omgvamp-hearthstone-v1.p.rapidapi.com/cards', config)
      .then((response) => {          
          this.$store.commit('setCards', response.data);
      }).catch(error => {
        console.log(error);
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  display: flex;
  align-items: center;
  justify-content: center;
}

body{
  background: #f2f2f2;
  font-family: 'Open Sans', sans-serif;
}

.search {
  width: 100%;
  position: relative;
  display: flex;
}

.searchTerm {
  width: 100%;
  border: 3px solid #00B4CC;
  border-right: none;
  padding: 5px;
  height: 20px;
  border-radius: 5px 0 0 5px;
  outline: none;
  color: #9DBFAF;
}

.searchTerm:focus{
  color: #00B4CC;
}

.searchButton {
  width: 40px;
  height: 36px;
  border: 1px solid #00B4CC;
  background: #00B4CC;
  text-align: center;
  color: #fff;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
  font-size: 20px;
}

/*Resize the wrap to see the search bar change!*/
.wrap{
  width: 30%;
  margin-left: 850px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
