<template>
  <div>

    <div class="small-container categorisection">
        <div class="row-2">
            <h2> All Product</h2>
            <select name="" id="sortering">
                <option value="">Default Shorting</option>
                <option value="alphabet">Short by Alphabet</option>
                <option value="lowprice">Short by lowest price first</option>
                <option value="expensive">Short by expensive first</option>
        
            </select>
        </div>

         <div class="row">
            <div class="categories-tabs">
                <span class="tab-item categories-selected active" data-target="all">All</span>
                <span class="tab-item" data-target="samsung">samsung</span>
                <span class="tab-item" data-target="apple">apple</span>
                <span class="tab-item" data-target="huawei">huawei</span>
                <span class="tab-item" data-target="xiaomi">xiaomi</span>
                <span class="tab-item" data-target="nokia">nokia</span>
                <span class="tab-item" data-target="lenovo">lenovo</span>
                <span class="tab-item" data-target="oneplus">one plus</span>
                <span class="tab-item" data-target="oppo">oppo</span>
            </div>
        </div>
        
        <h2 class="title" id="categorititle">Products</h2>

        <div class="allphoneitems">
           <div class="col-4" v-for="phone in allphone" :key="phone.id" :data-target="phone.brand">
                <img v-on:click="openpopup()" :src="require(`../assets${phone.image}.png`)">
                <h5>Article Nr : <span class="articlenr">{{phone.id}}</span></h5>
                 <h4>{{phone.brand}} - {{phone.title}}</h4>
                <p>Kr.<span class="price">{{phone.price}}</span></p>
                   <a v-on:click="addtocart(phone)">
                    <span></span>
                    <span></span>
                    <span></span>
                    <span></span>
                    Add to Cart
                 </a>
            </div>
      </div>
    </div>
  </div>
</template>
<script>
import { bus } from '../main'
export default {
  name: 'Showcase',
  
  computed: {

    header: function (item) {
  
      return item}
    },


  data(){
    return{
  
      sorted:[]
    
    }},

  props: ["allphone"],

  methods: {
    updatecartdetails: function(){
        this.$root.$emit('updatecard') 
        },
      

    getPic(image) {
    return '../assets/' + image.image + '.png'; },
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

    openpopup(){

        this.$emit("openpop", true)
    }

  },

    mounted:function(){
        
  	const filterContainer = document.querySelector(".categories-tabs");
  	const categorititle = document.querySelector("#categorititle");
    const phoneitems = document.querySelectorAll(".col-4");

   this.allphone
  	const sortering = document.querySelector("#sortering");
    sortering.addEventListener("change", (e) =>{
            console.log(e.target.value);

            if(e.target.value == "alphabet"){
                this.allphone.sort((a, b) => a.title.localeCompare(b.title))
            }
            else if(e.target.value == "lowprice"){
                this.allphone.sort((a, b) => a.price - b.price)
            }
            else if(e.target.value == "expensive"){
                this.allphone.sort((a, b) => b.price-a.price);
                
            }

             
    })


      filterContainer.addEventListener("click", (event)=>{


        if(event.target.classList.contains("tab-item") && 
       	!event.target.classList.contains("active")){

            filterContainer.querySelector(".active").classList.remove("active");
            event.target.classList.add("active");
            const target = event.target.getAttribute("data-target");

            categorititle.innerHTML = target.toUpperCase();
            phoneitems.forEach((item) =>{
           
           if(target === item.getAttribute("data-target") || target === 'all'){
            
           	  item.classList.remove("hide");
           	  item.classList.add("show");
           }
           else{
        
           	  item.classList.remove("show");
           	  item.classList.add("hide");
           }
       	 })
           }})


        // här börjar popup
         const  allphoneitems = document.querySelector(".allphoneitems");
        allphoneitems.addEventListener("click", (event) =>{
        
            bus.$emit('changeIt', event.target.closest(".col-4"))
     })     
       
       
       
       
       },
}
</script>

<style scoped>



/* ---------------------------------------------Tabs start */

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


.col-4{
    cursor: pointer;
}

.categorisection .col-4.hide{
   display: none;
}
.categorisection .col-4.show{
   display: block;
   animation: fadeInTop 0.5s ease;
}

.active{
    background: #ff523b;
   
}

.categories-selected{
    border: 2px solid #ff523b;
    padding: .2rem .6rem; 
    border-radius: 2rem;
    
}
.categories-tabs span{ 
    margin: 1rem;
    border: 2px solid #ff523b;
    padding: .2rem .6rem; 
    border-radius: 2rem;
    transition: background .5s ease-in-out;
    line-height: 60px;
    flex-wrap: wrap;
}
.categories-tabs span:last-child{
    margin-right: 0;
}

.categories-tabs span:hover{
    background: #ff523b;
    color:white;
    cursor: pointer;
}

/* ---------------------------------------------Tabs end */


.row-2{
    display: flex;
    justify-content: space-between;
    margin: 100px auto 50px;

}


.col-4{
    flex-basis: 25%;
    padding: 10px;
    min-width: 200px;
    margin-bottom: 50px;
    transition: transform 0.5s;
}

.allphoneitems{
    display: flex;
    align-items: flex-end;
    flex-wrap: wrap;
}

.allphoneitems .col-4 img{

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

.col-4 p{
    font-size: 14px;
}

.rating{
    color: #ff523b;
}

.col-4:hover{
    transform: translateY(-15px);
}


select{
    border: 2px solid #ec533e;
    color: black;

    border-radius: .5rem;
    text-align: center;

}

select:focus{
    outline: none;
}

</style>