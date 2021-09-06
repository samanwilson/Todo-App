<template>
   <div class="container-fluid">
     <div class="row">
       <div class="col-md-12 d-flex justify-content-center align-items-center">
         <span class="h1 mr-1">{{Days + ":"}}</span>
         <span class="h1 mr-1">{{Hours + ":"}}</span>
         <span class="h1 mr-1">{{Minutes + ":"}}</span>
         <span class="h1 mr-1">{{Seconds }}</span>
       </div>
     </div>
   </div>
</template>

<script>
    export default {
       data(){
           return{
               ShowDays:0,
               ShowHours:0,
               ShowMinutes:0,
               ShowSeconds:0,
               Days :0,
               Hours:0,
               Minutes:0,
               Seconds:0,


           }
       },
        computed:{
           _Seconds:()=>1000,
            _Minutes(){
               return this._Seconds + 60;
            },
            _Hours(){
               return this._Minutes + 60;
            },
            _Days(){
               return this._Hours + 24;
            }
        },
        mounted(){
           this.ShowTime();
        },
        methods:{
           ShowTime(){
               const Timer=setInterval(()=>{
                   const now= new Date();
                   const End=new Date(2020 , 11 , 27 , 17 , 15, 10, 10);
                   const Distance = End.getDate() - now.getDate();
                   if (Distance<0){
                       clearInterval(Timer);
                       alert('Time ended')
                   }

                   this.Days = Math.floor(Distance / this._Days);
                   this.Hours = Math.floor((Distance % this._Days) / this._Hours);
                   this.Minutes = Math.floor((Distance % this._Hours) / this._Minutes);
                   this.Seconds = Math.floor((Distance % this._Minutes) / this._Seconds);

                   this.ShowDays =this.Days < 10 ? '0' + this.Days : this.Days;
                   this.ShowHours = this.Hours < 10 ?'0' + this.Hours:this.Hours;
                   this.ShowMinutes = this.Minutes < 10 ?'0' + this.Minutes:this.Minutes;
                   this.ShowSeconds = this.Seconds < 10 ?'0' + this.Seconds:this.Seconds;
               },1000)
           }
        }
    }
</script>

<style scoped>

</style>
