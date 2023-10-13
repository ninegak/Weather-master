<script>
export default (await import('vue')).defineComponent({
    name: 'myWeather',
    components: {
    },
})
  </script>

<template>
  <div class="days-tab text-center">
    <div class="loading">Loading</div>
    <ul class="p-0">
        <li class="li_active">
            <div class="py-3">icon</div>
            <div class="py-3">day</div>
            <div class="py-3">120c</div>
         </li>
         <li class="li_active">
            <div class="py-3">icon</div>
            <div class="py-3">day</div>
            <div class="py-3">120c</div>
         </li>
         <li class="li_active">
            <div class="py-3">icon</div>
            <div class="py-3">day</div>
            <div class="py-3">120c</div>
         </li>
         <li class="li_active">
            <div class="py-3">icon</div>
            <div class="py-3">day</div>
            <div class="py-3">120c</div>
         </li>
    </ul>
  </div>
</template>

<style>
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
