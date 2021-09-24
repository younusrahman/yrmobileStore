<template>
 <div class="small-container">
        <h2 class="title">Latest Products</h2>
        <div class="row allphoneitems">
            <div class="col-4 latestproduct" v-for="phone in allphone" :key="phone.id" :data-target="phone.brand" v-if="phone.latest">
                <img v-on:click="openpopup()" :src="require(`../assets${phone.image}.png`)">
                 <h5>Article Nr : <span class="articlenr">{{phone.id}}</span></h5>
                 <h4>{{phone.brand}} - {{phone.title}}</h4>
                <p>Kr.<span class="price">{{phone.price}}</span></p>
 
                <a v-on:click="addtocart(phone)" >Add to Cart</a>
                
            </div>
        </div>

        <!-- ------------------------------------------------------Latest product -->
        <h2 class="title">Offer - Hurry Up</h2>
        <div class="row allphoneitems">
            <div class="col-4 exclusivoffer" v-for="phone in allphone" :key="phone.id" :data-target="phone.brand" v-if="phone.anyoffer >= 1">
                <img v-on:click="openpopup()" :src="require(`../assets${phone.image}.png`)">
                 <h5>Article Nr : <span class="articlenr">{{phone.id}}</span></h5>
                 <h4>{{phone.brand}} - {{phone.title}}</h4>
                 <div id="newNoldPrice">
                    <p id="newprice">Kr.<span class="price">{{phone.anyoffer}}</span></p>
                    <p id="oldprice">Kr.<span class="price">{{phone.price}}</span></p>
                 </div>
                <a v-on:click="addtocart(phone)" >Add to Cart</a>
                
            </div>
        </div>
    </div>

</template>
<script>
import { bus } from '../main'
export default {    
  name: 'Exclusiv',
  data(){
      return{
          arr:[],
        selectedPHId : 0,
        }
    },



  
  props: ["allphone"],

   created (){

       
    bus.$on('changeIt', (data) => {
    //   this.selectedPHId = data.querySelector("#showcaseid").innerHTML
    //   console.log(this.selectedPHId)
    })
  },

  mounted: function(){
        
        const  allphoneitems = document.querySelector(".allphoneitems");
        allphoneitems.addEventListener("click", (event) =>{

            
        
            bus.$emit('changeIt', event.target.closest(".col-4"))


     })  
  },

   methods: {
        updatecartdetails: function(){
        this.$root.$emit('updatecard') 
        },
            
    openpopup(){
            this.$emit("openpop", true)
        
    },

        getPic(image) {
    return '../assets/' + image.image + '.png';},

    
addtocart(prod){


         
        for (let i = 0; i < this.$store.length; i++) { 
               if(this.$store[i].product.id == prod.id)
               {
                   this.$store[i].Quantity++
                   this.updatecartdetails()
                   return;
               }
            }
        this.$store.push({Quantity:1, product: prod});
    },


    },
  
}
</script>


<style scoped>


a{
    position: relative;
    display: inline-block;
    padding: 15px 15px;
    margin: 40px 0;
    color: #ff523b;
    text-decoration: none;
    text-transform: uppercase;
    transition: 0.5s;
    letter-spacing: 4px;
    overflow: hidden;
    margin-right: 50px;
    font-size: 1rem;
    text-align: center;
   
}
a:hover{
    background: #ff523b;
    color: #050801;
    box-shadow: 0 0 5px #ff523b,
                0 0 25px #ff523b,
                0 0 50px #ff523b,
                0 0 200px #ff523b;
     -webkit-box-reflect:below 1px linear-gradient(transparent, #0005);
}
a:nth-child(1){
    filter: hue-rotate(270deg);
}
a:nth-child(2){
    filter: hue-rotate(110deg);
}
a span{
    position: absolute;
    display: block;
}
a span:nth-child(1){
    top: 0;
    left: 0;
    width: 100%;
    height: 2px;
    background: linear-gradient(90deg,transparent,#ff523b);
    animation: animate1 1s linear infinite;
}

span{
    font-weight: bold;
}


#newprice{
    font-weight: bold;
    color: red;
    font-size: 1.4rem;
}

#oldprice{
    font-weight: bold;

    font-size: 1rem;
    text-decoration: line-through;
}

#newNoldPrice{
    display: flex;
    justify-content: space-between;
}


.col-4{
    flex-basis: 25%;
    padding: 10px;
    min-width: 200px;
    margin-bottom: 50px;
    transition: transform 0.5s;
    cursor: pointer;
}

.col-4 img{
    width: 100%;
}

.col-4{
    flex-basis: 25%;
    padding: 10px;
    min-width: 200px;
    margin-bottom: 50px;
}
.col-4 img{
    width: 100%;
}

.title{
    margin-top: 2rem;
}


.col-4 p{
    font-size: 14px;
}

.rating{
    color: #ff523b;
}

.col-4:hover{
    transform: translateY(-15px);
}

</style>
