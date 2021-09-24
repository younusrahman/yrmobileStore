<template>
  <div id="app">
    <Navbar v-on:selecteditem="selectedmenuitem"/>
    <Home v-if="this.choosenmenu !== '2' && this.choosenmenu !== '3' && this.choosenmenu !== '4' && this.choosenmenu !== '5' && this.choosenmenu !== 'Popup'"  />
    <PhShowcase v-if="this.choosenmenu == '2'" v-on:openpop="openpopup" v-bind:header="header" v-bind:allphone="allphonedata"/>
    <ProductDetails   v-show="this.choosenmenu === 'Popup'"  v-bind:header="header" v-bind:allphone="allphonedata"/>
    <Exclusiv  v-show="this.choosenmenu === '3'" v-bind:header="header" v-bind:allphone="allphonedata"/>
    <Shoppingcart v-show="this.choosenmenu === '5'"/>
    <Authorizing v-show="this.choosenmenu === '4'"/>
    <Brand v-show="this.choosenmenu == '2' || this.choosenmenu == '3' || this.choosenmenu == '4' || this.choosenmenu == '5'"/>
    <Footer></Footer>


  </div>
</template>
<script>
import Home from './assets/Home.vue';
import Navbar from './assets/Navbar.vue';
import PhShowcase from './assets/PhShowcase.vue';
import ProductDetails from './assets/ProductDetails.vue';
import Exclusiv from './assets/Exclusiv.vue';
import Shoppingcart from './assets/Shoppingcart.vue';
import Footer from './assets/PhFooter.vue';
import Brand from './assets/Brand.vue';
import Authorizing from './assets/Authorizing.vue';
import axios from 'axios'
export default {
  
  name: 'app',
  components: {
    Navbar,Home,PhShowcase, 
    ProductDetails,
    Exclusiv,
    Shoppingcart,
    Footer,
    Brand,
    Authorizing
    
    
  },
  data (){
    return {
      header:'initial header',
      hideall:false,
      choosenmenu: 1,
      allphonedata:[],
    }
  },
  methods: {
    selectedmenuitem : function (menuitem){ this.choosenmenu = menuitem;},

    openpopup: function(item){ 
        console.log( "here" )
      
      this.choosenmenu = "Popup"},

  },

  mounted:function(){
    

        axios.get("http://localhost:3000/products")
       .then(response =>{ this.allphonedata = response.data })},

    
  
  }
</script>
<style>




small{
    color: #555;
}


h1{
    margin: 1.2rem 0;
}

h4{
    color: #555;
    font-weight: normal;
}

ul{
  list-style-type: none;
}

li{
    list-style: none;
}


a{
    text-decoration: none;
    color: #555;
}

.container{
    max-width: 1300px;
    margin: auto;
    padding-left: 25px;
    padding-right: 25px;


}

.row{
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    justify-content: space-around;

}

.col-2{
    flex-basis: 50%;
    min-width: 300px;
    
}


.col-3{
    flex-basis: 30%;
    min-width: 250px;
    margin-bottom: 30px;
}


.small-container{
    max-width: 1080px;
    margin: auto;
    padding-left: 25px;
    padding-right: 25px;
}

.title{
    text-align: center;
    margin: 0 auto 80px;
    position: relative;
    line-height: 60px;
    color: #555;
}

.title::after{
    content: '';
    background: #ff523b;
    width: 80px;
    height: 5px;
    border-radius: 5px;
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
}

#app {

  display: flex;
  flex-direction:column;
  justify-content: center;
  align-content: center;

} 

/* -----------------------------------Button login */

button{
  
  color:#ff523b;
  border:none;
  position:relative;
  height:60px;
  font-size:1.6em;
  padding:0 2em;
  cursor:pointer;
  transition:800ms ease all;
  outline:none;
  background: white;
}
button:hover{
  background:transparent;
  
}
button:before,button:after{
  content:'';
  position:absolute;
  top:0;
  right:0;
  height:2px;
  width:0;
  background: #ff523b;
  transition:400ms ease all;
}
button:after{
  right:inherit;
  top:inherit;
  left:0;
  bottom:0;
}
button:hover:before,button:hover:after{
  width:100%;
  transition:800ms ease all;
}


</style>