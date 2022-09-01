<template lang="">

<div class="row">
   <div class="col-2"></div>
   <div class="col-4" style="backgroundColor: #7CB5EC ;height:150px;border-radius:30px; color:#fff;">
         <p style="text-align:center;font-weight:bold;font-size:25px;">le nombre des clients 
            <br/>
            <span style="font-size:50px;font-weight:bolder;">
               {{nombreclients}}
            </span>
         </p>
   </div> &nbsp; &nbsp;
   <div class="col-4" style="backgroundColor: #90ED7D ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">le nombre des commandes</p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_client" @keyup.enter="chercher"  placeholder="id client">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{nombrecommande}}</p>
   </div>
   <div class="col-2"></div>
</div>
<br/>
<div class="row">
   <div class="col-4"></div>
   <div class="col-4" style="backgroundColor: #434348 ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">Montant total payé </p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_client_montant" @keyup.enter="chercher_montant"  placeholder="id client">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{montanttotal}}&nbsp;$</p></div>
</div>
<br/>
    <div class="row">
        <div id = "container" style = "width: 550px; height: 400px; margin: 0 auto"></div>
        
    </div>
    <div>
            <footer1/>
    </div>
</template>
<script>
   import footer1 from './footer1.vue'
   import axios from 'axios'
   export default{
      components:{
         footer1
      },
      data(){
         return{
            nombreclients:null,
            id_client:null,
            nombrecommande:null,
            montanttotal:null,
            id_client_montant:null

         }
      },
      mounted () {
               axios
                  .get('http://127.0.0.1:8000/customer')
                  .then(res=>{
                     this.nombreclients=res.data
               }).catch(error=>{
                    console.log(error)
            })
         },
         methods:{
            chercher(){
               if(this.id_client!=""){
                  axios
                  .get(`http://localhost:8000/commande/${this.id_client}`)
                     .then(res=>{
                        this.nombrecommande=res.data
                        this.id_client=""
                  }).catch(error=>{
                       console.log(error)
               })
               
               }
               else{
                  console.log('not ok')
               }

            },
            chercher_montant(){
               if(this.id_client_montant!=""){
                  axios
                  .get(`http://localhost:8000/commande/montanttotal/${this.id_client_montant}`)
                     .then(res=>{
                        this.montanttotal=res.data
                        this.id_client_montant=""
                  }).catch(error=>{
                       console.log(error)
               })
               
               }
               else{
                  console.log('not ok')
               }
            }
         }

   }
$(document).ready(function() {  
            var chart = {
               type: 'bar'
            };
            var title = {
               text: 'nombre des clients par pays'   
            };
            var xAxis = {
               categories: ['Allemagne', 'Australie', 'Canada', 'États-Unis', 'France','Royaume-Uni'],
               title: {
                  text: null
               }
            };
            var yAxis = {
               min: 0,
               title: {
                  text: 'nombre (U)',
                  align: 'high'
               },
               labels: {
                  overflow: 'justify'
               }
            };
            var tooltip = {
               valueSuffix: ' U'
            };
            var plotOptions = {
               bar: {
                  dataLabels: {
                     enabled: true
                  }
               }
            };
            var legend = {
               layout: 'vertical',
               align: 'right',
               verticalAlign: 'top',
               x: -40,
               y: 100,
               floating: true,
               borderWidth: 1,
               
               backgroundColor: (
                  (Highcharts.theme && Highcharts.theme.legendBackgroundColor) ||
                     '#FFFFFF'),
               shadow: true
            };
            var credits = {
               enabled: false
            };
            var series = [
               {
                  name: 'Year 2011',
                  data: [167, 766, 165, 735, 137,171]
               }, 
               {
                  name: 'Year 2012',
                  data: [327, 1102, 171, 872, 345,392]
               }, 
               {
                  name: 'Year 2013',
                  data: [4806, 10752, 6630, 18310, 4747,5952]      
               },
               {
                  name: 'Year 2014',
                  data: [327, 725, 654, 1427, 329,391]      
               }
            ];
      
            var json = {};   
            json.chart = chart; 
            json.title = title;   
            
            json.tooltip = tooltip;
            json.xAxis = xAxis;
            json.yAxis = yAxis;  
            json.series = series;
            json.plotOptions = plotOptions;
            json.legend = legend;
            json.credits = credits;
            $('#container').highcharts(json);
         });
         
        
</script>
<style lang="">
    
</style>