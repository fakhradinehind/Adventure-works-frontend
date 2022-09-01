<template lang="">
    <div class="row">
   <div class="col-2"></div>
   <div class="col-4" style="backgroundColor: #7CB5EC ;height:150px;border-radius:30px; color:#fff;">
         <p style="text-align:center;font-weight:bold;font-size:25px;">le nombre des employes
            <br/>
            <span style="font-size:50px;font-weight:bolder;">
               {{nombreemployes}}
            </span>
         </p>
   </div> &nbsp; &nbsp;
   <div class="col-4" style="backgroundColor: #434348 ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">commandes traitées par employés </p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_employes" @keyup.enter="nombrecommandetraite"  placeholder="id client">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{nombrecommandetraitee}}</p>
    </div>
   <div class="col-2"></div>
</div>
<br/>
<div class="row">
   <div class="col-4"></div>
   
    <div class="col-4" style="backgroundColor: #90ED7D ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">Revenus par employes</p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_employes" @keyup.enter="revenusparemployes"  placeholder="id client">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{revenusemployes}}&nbsp;$</p>
   </div>
</div>
<br/>
<br/>
    <div class="row">
        <div id = "container" style = "width: 550px; height: 400px; margin: 0 auto"></div>
        
    </div>
   
</template>
<script>
  import axios from 'axios'
export default{
    data(){
        return{
            nombreemployes:null,
            revenusemployes:null,
            id_employes:null,
            nombrecommandetraitee:null
        }
    },
    mounted () {
               axios
                  .get('http://127.0.0.1:8000/employes')
                  .then(res=>{
                     this.nombreemployes=res.data
               }).catch(error=>{
                    console.log(error)
            })
         },
    methods:{
        revenusparemployes(){
            axios
                  .get(`http://127.0.0.1:8000/commandejoinemployes/revenusparemployes/${this.id_employes}`)
                  .then(res=>{
                     this.revenusemployes=res.data
               }).catch(error=>{
                    console.log(error)
            })
        },
        nombrecommandetraite(){
            axios
                  .get('http://127.0.0.1:8000/commandejoinemployes')
                  .then(res=>{
                     this.nombrecommandetraitee=res.data
               }).catch(error=>{
                    console.log(error)
            })
        }
    }
}


$(document).ready(function() {  
            var chart = {
               type: 'column'
            };
            var title = {
               text: 'Nombre des employes par mois et par pays'   
            };
            var subtitle = {
               text: ''  
            };
            var xAxis = {
               categories: ['Jan','Feb','Mar','Apr','May','Jun','Jul',
                  'Aug','Sep','Oct','Nov','Dec'],
               crosshair: true
            };
            var yAxis = {
               min: 0,
               title: {
                  text: 'nombre'         
               }      
            };
            var tooltip = {
               headerFormat: '<span style = "font-size:10px">{point.key}</span><table>',
               pointFormat: '<tr><td style = "color:{series.color};padding:0">{series.name}: </td>' +
                  '<td style = "padding:0"><b>{point.y:.1f} mm</b></td></tr>',
               footerFormat: '</table>',
               shared: true,
               useHTML: true
            };
            var plotOptions = {
               column: {
                  pointPadding: 0.2,
                  borderWidth: 0
               }
            };  
            var credits = {
               enabled: false
            };
            var series= [
               {
                  name: 'France',
                  data: [49.9, 71.5, 106.4, 129.2, 144.0, 176.0, 135.6,
                     148.5, 216.4, 194.1, 95.6, 54.4]
               }, 
               {
                  name: 'Canada',
                  data: [83.6, 78.8, 98.5, 93.4, 106.0, 84.5, 105.0, 104.3,
                     91.2, 83.5, 106.6, 92.3]
               }, 
               {
                  name: 'Australie',
                  data: [48.9, 38.8, 39.3, 41.4, 47.0, 48.3, 59.0, 59.6,
                     52.4, 65.2, 59.3, 51.2]
               }, 
               {
                  name: 'Allemagne',
                  data: [42.4, 33.2, 34.5, 39.7, 52.6, 75.5, 57.4, 60.4,
                     47.6, 39.1, 46.8, 51.1]
               }
            ];     
         
            var json = {};   
            json.chart = chart; 
            json.title = title;   
            json.subtitle = subtitle; 
            json.tooltip = tooltip;
            json.xAxis = xAxis;
            json.yAxis = yAxis;  
            json.series = series;
            json.plotOptions = plotOptions;  
            json.credits = credits;
            $('#container').highcharts(json);
  
         });
</script>
<style lang="">
    
</style>