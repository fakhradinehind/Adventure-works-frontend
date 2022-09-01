<template lang="">
   
   <div class="row">
   <div class="col-2"></div>
   <div class="col-4" style="backgroundColor: #7CB5EC ;height:150px;border-radius:30px; color:#fff;">
         <p style="text-align:center;font-weight:bold;font-size:25px;">le nombre des produits 
            <br/>
            <span style="font-size:50px;font-weight:bolder;">
               {{nombreproduits}}
            </span>
         </p>
   </div> &nbsp; &nbsp;
   <div class="col-4" style="backgroundColor: #90ED7D ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">Revenus par produits</p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_produit" @keyup.enter="revenusproduit"  placeholder="id produit">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{revenusparproduit}}&nbsp;$</p>
   </div>
   <div class="col-2"></div>
</div>
<br/>
<div class="row">
   <div class="col-2"></div>
   <div class="col-4" style="backgroundColor: #7CB5EC ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">Nombre commande par produit</p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_produit" @keyup.enter="nombrecommandeparproduit"  placeholder="id produit">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{nombreproduit}}</p>
   </div>&nbsp; &nbsp;
   <div class="col-4" style="backgroundColor: #90ED7D ;height:150px;border-radius:30px; color:#fff;">
      <p style="text-align:center;font-weight:bold;font-size:25px;">Nombre de client par produit </p>
      <input type="number"  min="1" style="margin-left:120px;border-radius:10px;" v-model="id_produit" @keyup.enter="nombreclientparproduit"  placeholder="id produit">
      <p style="text-align:center;font-size:50px;font-weight:bolder;">{{nombreclientproduit}}</p>
   </div>
   <div class="col-2"></div>
</div>
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
            nombreproduits:null,
            id_produit:null,
            revenusparproduit:null,
            nombreproduit:null,
            nombreclientproduit:null
         }
      },
      mounted () {
    axios
      .get('http://127.0.0.1:8000/product')
      .then(res=>{
       this.nombreproduits=res.data
            }).catch(error=>{
       console.log(error)
            })
      },
      methods:{
         revenusproduit(){
            axios
               .get(`http://127.0.0.1:8000/commandejoinproduct/sommerevenus/${this.id_produit}`)
               .then(res=>{
                     this.revenusparproduit=res.data
                        }).catch(error=>{
                     console.log(error)
            })
         },
         nombrecommandeparproduit(){
            axios
               .get(`http://127.0.0.1:8000/commandejoinproduct/nombrecommandeparproduit/${this.id_produit}`)
               .then(res=>{
                     this.nombreproduit=res.data
                        }).catch(error=>{
                     console.log(error)
            })
         },
         nombreclientparproduit(){
            axios
               .get(`http://127.0.0.1:8000/commande/nombreclientparproduit/${this.id_produit}`)
               .then(res=>{
                     this.nombreclientproduit=res.data
                        }).catch(error=>{
                     console.log(error)
            })
         }
      }
   }
$(document).ready(function() {
            var chart = {
               plotBackgroundColor: null,
               plotBorderWidth: null,
               plotShadow: false
            };
            var title = {
               text: 'pourcentage des produits par category'   
            };
            var tooltip = {
               pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
            };
            var plotOptions = {
               pie: {
                  allowPointSelect: true,
                  cursor: 'pointer',
                  
                  dataLabels: {
                     enabled: true,
                     format: '<b>{point.name}%</b>: {point.percentage:.1f} %',
                     style: {
                        color: (Highcharts.theme && Highcharts.theme.contrastTextColor)||
                        'black'
                     }
                  }
               }
            };
            var series = [{
               type: 'pie',
               name: 'Browser share',
               data: [
                  ['Santé',   45.0],
                  ['beauté',       26.8],
                  
                  
                  ['cosmétiques',    8.5],
                  ['bio',     6.2],
                  ['Others',   0.7]
               ]
            }];
            var json = {};   
            json.chart = chart; 
            json.title = title;     
            json.tooltip = tooltip;  
            json.series = series;
            json.plotOptions = plotOptions;
            $('#container').highcharts(json);  
         });
</script>
<style lang="">
    
</style>