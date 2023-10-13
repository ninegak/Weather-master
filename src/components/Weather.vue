<script>
import axios from 'axios';
import DaysWeather from './DaysWeather.vue';
export default (await import('vue')).defineComponent({
    name: 'myWeather',
    components: {
        DaysWeather,
        axios
    },
    props:{
        city: String,
    },
    data(){
        return{
            temperature: null,
            description: null,
            iconUrl: null,
            date: null,
            time: null,
            name: null,
            country: null,
            monthNames: ["january","February","March","April","May","June","july","August","September","October","November","December"]
    }
    },
    async created(){
        const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=ae43c233b84d7d9919cfe73d689793e8`);
        const weatherData = response.data;
        this.temperature = weatherData.main.temp;
        this.description = weatherData.weather[0].description;
        this.name = weatherData.name;
        this.iconUrl = `https://api.openweathermap.org/img/w/${weatherData.weather[0].icon}.png`;
        const d = new Date();
        this.date = d.getDate() + '-' + this.monthNames[d.getMonth()] + '-' + d.getFullYear();
        this.time = d.getHours() + ':' + d.getMinutes() + ':' +d.getSeconds();
        console.log(response);
        console.log(this.city);
    }
})
  </script>

<template>
  <div class="container p-0">
    <div class="d-flex">
        <div class="card main-div w-100">
            <div class="p-3">
                <h2 class="mb-1 day">Tuesday</h2>
                <p class="text-light data mb-o">{{date}}</p>
                <small>{{time}}</small>
                <h2 class="place"><i class="fa fa-location">{{ name }}<small>{{ country }}</small></i></h2>
            <div class="temp"></div>
            <h1 class="weather-temp">{{ temperature }}&deg;</h1>

            <h2 class="text-ligt">{{ description }}<img :src="iconUrl"></h2>

          </div>
        </div>
    </div>
  </div>
  <div class="card card-2 w-100">
    <table class="m-4">
      <tbody>
        <tr>
        <th>Sea Level</th>
        <td>100</td>
      </tr>
      <tr>
        <th>Sea Level</th>
        <td>100</td>
      </tr>
      <tr>
        <th>Sea Level</th>
        <td>100</td>
      </tr>
      <tr>
        <th>Sea Level</th>
        <td>100</td>
      </tr>
      </tbody>
    </table>
    <div id="div_Form" class="d-flex m-3 justify-content">
      <form action="">
        <input type="button" value="Change Location" class="btn change-btn-primary">
      </form>
    </div>
  </div>
</template>
<style>
    body{
        background-color: #343d4b;
    }
.weather-temp{
    margin:0%;
    font-weight: 700;
    font-size: 4cm;
}
h2.mp-1.day{
    font-size: 3rem;
    font-weight: 400;
}
.main-div{
    border-radius: 20px;
    color:#fff;
    background-image:url("");
    background-size: cover;
    background-position: center;
    background-blend-mode: overlay;
    background-color: rgba(0,0,0,0.5);
    background-repeat: no-repeat;
} 
.temp{
    position: absolute;
    bottom: 0;
}
.main-div-hover{
    transform: scale(1.1);
    transition: transform 0.5s ease;
    z-index: 1;
}
.card-2{
    background-color: #212730;
    border-radius: 20px;
}
.card-details{
    margin-left:19px;
}
.h1_left{
    position: absolute;
    bottom:25px;
    left:16px;
    font-size:3vw;
    line-height: 1.2;
}
.h3_Left{
    position:absolute;
    left: 16px;
    font-size: 2vw;
    line-height: 0.5;
}
.h3_Left small{
    font-size: 1rem;
}
table{
    position:relative;
    left:15px;
    border-collapse: separate;
    border-spacing: 15px;
    width:85%;
    text-align:left;
    max-width:600px;
    margin:0 auto;
}
td{
    font-size:18px;
    color:#fff;
}
td{
    text-align: right;
}
.change_btn{
    background-image: linear-gradient(to right, cyan, magenta);
}
</style>
