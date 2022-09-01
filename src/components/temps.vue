<template lang="">
    <div class="row">
   <div class="col-2"></div>
   <div class="col-4" style="backgroundColor: #7CB5EC ;height:150px;border-radius:30px; color:#fff;">
            <div class="form-group">
                <label for="year" style="text-align:center;font-weight:bold;font-size:25px;" >Calculer le revenus par annee</label>
                <select id="year" class="form-control" v-model="year" @keyup.enter="sommerevenusyear">
                    <option>2011</option>
                    <option>2012</option>
                    <option>2013</option>
                    <option>2014</option>
                </select>
                <br/>
                <p class="button">
                    <button class="btn btn-primary" @click="sommerevenusyear">calculer</button>
                    &nbsp;<span>{{sommeyear}}&nbsp;$</span>
                </p>
            </div>   
   </div> &nbsp; &nbsp;
   <div class="col-4" style="backgroundColor: #90ED7D ;height:150px;border-radius:30px; color:#fff;">
    <div class="form-group">
                <label for="month" style="text-align:center;font-weight:bold;font-size:25px;">Calculer le revenus par mois</label>
                <select id="month" class="form-control" v-model="month">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                    <option>5</option>
                    <option>6</option>
                    <option>7</option>
                    <option>8</option>
                    <option>9</option>
                    <option>10</option>
                    <option>11</option>
                    <option>12</option>
                </select>
                <br/>
                <p class="button">
                    <button class="btn btn-primary"  @click="sommerevenusmonth">checher</button>
                    &nbsp;<span>{{sommemonth}}&nbsp;$</span>
                </p>
            </div> 
   </div>
   <div class="col-2"></div>
</div>
<br/>
<div class="row">
   <div class="col-2"></div>
   <div class="col-4" style="backgroundColor: #7CB5EC ;height:150px;border-radius:30px; color:#fff;">
            <div class="form-group">
                <label for="semestre" style="text-align:center;font-weight:bold;font-size:25px;" >Calculer le revenus par semestre</label>
                <select id="semestre" class="form-control" v-model="semestre" @keyup.enter="sommerevenussemestre">
                    <option>1</option>
                    <option>2</option>
                </select>
                <br/>
                <p class="button">
                    <button class="btn btn-primary" @click="sommerevenussemestre">calculer</button>
                    &nbsp;<span>{{sommesemestre}}&nbsp;$</span>
                </p>
            </div>   
   </div> &nbsp; &nbsp;
   <div class="col-4" style="backgroundColor: #90ED7D ;height:150px;border-radius:30px; color:#fff;">
    <div class="form-group">
                <label for="trimestre" style="text-align:center;font-weight:bold;font-size:25px;">Calculer le revenus par trimestre</label>
                <select id="trimestre" class="form-control" v-model="trimestre">
                    <option>1</option>
                    <option>2</option>
                    <option>3</option>
                    <option>4</option>
                </select>
                <br/>
                <p class="button">
                    <button class="btn btn-primary"  @click="sommerevenustrimestre">checher</button>
                    &nbsp;<span>{{sommetrimestre}}&nbsp;$</span>
                </p>
            </div> 
   </div>
   <div class="col-2"></div>
</div>
<br/>
<br/>
<footer1/>
</template>
<script>
    import footer1 from '../components/footer1.vue'
    import axios from 'axios'
export default {
    data(){
        return{
                year:2011,
                sommeyear:null,
                month:1,
                sommemonth:null,
                sommesemestre:null,
                semestre:1,
                sommetrimestre:null,
                trimestre:1

        }
    },
    components: {
        footer1
    },
    methods:{
        sommerevenusyear(){
            axios
                  .get(`http://127.0.0.1:8000/commandejointemps/year/${this.year}`)
                     .then(res=>{
                        this.sommeyear=res.data
                        
                  }).catch(error=>{
                       console.log(error)
               })
        },
        sommerevenusmonth(){
            axios
                  .get(`http://127.0.0.1:8000/commandejointemps/month/${this.month}`)
                     .then(res=>{
                        this.sommemonth=res.data
                        
                  }).catch(error=>{
                       console.log(error)
               })
        },
        sommerevenussemestre(){
            
            axios
                  .get(`http://127.0.0.1:8000/commandejointemps/semestre/${this.semestre}`)
                     .then(res=>{
                        this.sommesemestre=res.data
                        
                  }).catch(error=>{
                       console.log(error)
               })
        },
        sommerevenustrimestre(){
            axios
                  .get(`http://127.0.0.1:8000/commandejointemps/trimestre/${this.trimestre}`)
                     .then(res=>{
                        this.sommetrimestre=res.data
                        
                  }).catch(error=>{
                       console.log(error)
               })
        }
    }
}
</script>
<style>
    .button{
        text-align: center;
    }
</style>