<template>

    <div class="small-container single-product">

        <div class="small-container">
            <div class="row" v-for="phone in allphone" :key="phone.id" v-show="phone.id == selectedPHId">
                <div class="col-2" id="Product-img">

                    <img :src="require(`../assets${phone.image}.png`)">                  
                </div>
                <div class="col-2">

              
                    <h1> {{phone.brand}} - {{phone.title}}</h1>
                    <h4>Kr.{{phone.price}}</h4>
                    <select>
                        <option value="" name="" id=""  v-for="c in phone.color" :key="c.id">{{c}}</option>
                        
                    </select>
                    <input class="quantity" type="number"  v-model="antal" min="1" v-bind:max="phone.stockstatic">
                    
                    <h3>Product Details <i class="fa fa-indent"></i> </h3>
                    <br>
                    <p>
                        {{phone.ProductDetails}}
                    </p>
                    <a v-on:click="addtocart(phone)" >Add to Cart</a>

                </div>
            </div>
        </div>

   
        </div>
</template>
<script>
import { bus } from '../main';
export default {
  name: 'Details',


  data(){
        return{
            cartdetails:{},
            antal : 1,
            selectedPHId : 0}
        },
  props: ["allphone"],

  methods:{
      updatecartdetails: function(){
          this.$root.$emit('updatecard')
          },
      getPic(image) {
    return '../assets/' + image.image + '.png'},


    addtocart(prod){
        for (let i = 0; i < this.$store.length; i++) {
            if(this.$store[i].product.id == prod.id)
              {
                   this.$store[i].Quantity += parseInt(this.antal);
                   this.updatecartdetails()
                   this.antal=1
                   return;
                }}

        this.$store.push({Quantity:this.antal, product: prod});
        this.antal=1}},
  
    created (){
    bus.$on('changeIt', (data) => {
      this.selectedPHId = data.querySelector(".articlenr").innerHTML})}}

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
    cursor: pointer;
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

.single-product{
    margin-top: 80px;

}

select{
    border: 1px solid #ff523b;
}
.single-product .col-2 img{
    width: 100%;
 
}

.single-product .col-2{
    padding: 20px;
}

.single-product h4{
    margin: 20px 0;
    font-size: 22px;
    font-weight: bold;
}

.single-product select{
    display: block;
    padding: 10px;
    margin-top: 20px;
    
}
.single-product input{
    width: 50px;
    height: 40px;
    padding-left: 10px;
    font-size: 20px;
    margin-right: 10px ;
    margin: 20px 20px 20px 0;
    border: 1px solid #ff523b;

}

select, input:focus{
    outline: none;
}


.small-img-row{
    display: flex;
    justify-content: space-between;
}


.btn-1 a{
  text-decoration: none;
  border: 2px solid #ff523b;
  padding: 15px;
  color: black;
  text-transform: uppercase;
  letter-spacing: 2px;
  position: relative;
  display: inline-block;
  cursor: pointer;
}

.btn-1 span {
  position: relative;
  z-index: 3;
  
  
}

/* Button 1 styles */

.btn-1 a::before {
  content: "";
  position: absolute;
  top: 5px;
  left: -2px;
  width: calc(100% + 6px);
  height: calc(100% - 10px);
  background-color: #ffffff;
  transition: all 0.5s ease-in-out;
  transform: scaleY(1);
  
}

.btn-1 a:hover::before {
  transform: scaleY(0);
  
}

.btn-1 a::after {
  content: "";
  position: absolute;
  left: 5px;
  top: -5px;
  width: calc(100% - 10px);
  height: calc(100% + 10px);
  background-color: #ffffff;
  transition: all 0.5s ease-in-out;
  transform: scaleX(1);
}


.btn-1 a:hover::after{
  transform: scaleX(0);
  
}


</style>
