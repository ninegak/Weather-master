<script>
import Weather from './components/Weather.vue';

export default {
  name: 'App',
  components: {
    Weather,
  },
  data() {
    return {
      city: '',
      showWeather: false,
    };
  },
  methods: {
    async searchWeather() {
      this.showWeather = false;
      await this.$nextTick();
      this.showWeather = true;
    },
  },
};
</script>
  <template>
  <div class="header container h-100 p-5">
    <h1 class="mb-5">Weather App</h1>
    <div class="d-flex justify-content-center h-100">
      <div class="searchbar w-50 mx-2">
        <input type="text" class="input form-control" v-model="city" placeholder="Enter a City">
      </div>
      <button class="btn-search btn btn-primary" @click="searchWeather">Search <i class="fas fa-search"></i></button>
    </div>
    <Weather :city="city" v-if="showWeather"></Weather>
  </div>
</template>

<style>
body{
  background-color: black
}
.header{
  background-color:black;
  border-radius: 20px;
  color:white;
  text-align: center;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  margin-top: 5rem;
  
}
.btn-search{
  background-image: linear-gradient(to right, cyan,magenta);
}
.day-tab{
  width:90%;
  box-shadow: 0 4px 8px 0 rgba(0, 0,0,2), 0 6px 20px 0 rgba(0, 0, 0, 19);
  width:90%;
  margin:auto;
}
.Loading{
  color:white
}
ul{
  margin:0;
}
li{
  display: inline-block;
  list-style:name;
  height: 100%;
  width:21%;
  max-width: 21%;
  line-height: 1.2;
}
span{
  display:block;
  margin-bottom:5px;
  font:100% sans-serif;
  height: 35px;
}
.li_active{
  background: #253d5c;
  color:#222831;
  border-radius: 10px;
  margin: 0.5rm;
  color:#fff;
  font-weight:600;
}
.li_active:hover{
  transform: scale(1.2);
  transition: transform 0.1s ease;
}
.li_active_temp{
  display:inline-block;
  background-color: #222831;
  color:#fff;
  transition: background-color 0.5s;
  border-radius: 10px;
}

</style>
