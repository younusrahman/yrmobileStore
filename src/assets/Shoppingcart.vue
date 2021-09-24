<template>
    <div class="small-container">
        <h2 class="title"> Kassa</h2>
        <div class="row">

            <table>
        <tr>
            <th>Product</th>
            <th>Quantity</th>
            <th>Subtotal</th>
        </tr>
        <tr class="cartphone"  v-for="p in cartdetails" :data-target="p.product.id">
            <td class="cart-info">
                <img :src="require(`../assets${p.product.image}.png`)">
                <div>
                    <p>{{p.product.brand}} - {{p.product.title}}</p>
                    <a class="removebt" @click="removeitem(p.product.id)" :artikenr="p.product.id" href="#">Remove</a>
                </div>
            </td>
            <td><input type="number" min="1" :value="p.Quantity" :id="p.product.id" @change="changedQuantity(p)"></td>
            <td v-if="p.product.anyoffer == 0">{{p.product.price}} .Kr</td>
            <td id="Offerprice" v-if="p.product.anyoffer > 0">{{p.product.anyoffer}}.Kr</td>
        </tr>
    </table>
        </div>
     <div class="row1">
         
        <div>
            <table>
                <tr id="tax">
                    <td>Tax</td>
                    <td>{{moms}} .kr</td>
                </tr>
                <tr id="summa">
                    <td>Total</td>
                    <td>{{totalprice}} .kr</td>
                </tr>
            </table>
        </div>
    </div>
        <a v-on:click="paid()"  v-show="cartdetails.length > 0">Continue to payment</a>
    </div>

</template>
<script>


 

 
export default {
  name: 'Details',


  data(){
      return{
          cartdetails : [],
          totalprice : 0,
          moms:0,
            antal:0,
          sameproduct:0
      
      }},

  watch: {
    cartdetails: function () {
        this.getcardetails();
            

        }},

 methods: {

     getcardetails: function(){

                     let tprice = 0
            let tmoms = 0

            this.$store.forEach((element, index) =>{
                if(element.product.anyoffer > 0){
                    tprice += (element.product.anyoffer * element.Quantity)
                }
                else{
                     tprice += (element.product.price * element.Quantity)
                }
                    
                

            });
     
            tmoms = tprice * 0.2;
            
            this.totalprice = Math.round(tprice);
            this.moms = Math.round(tmoms);

     },

     changedQuantity: function(ph){

            const gotinput = document.getElementById(ph.product.id);
            ph.Quantity = gotinput.value
            this.getcardetails();
                 
     },


     paid: ()=>{

         Swal.fire(
        'Good job!',
        'your payment has been confirmed!',
        'success'
                )
    setTimeout(function(){
        window.location.reload();
    }, 2000)

                
     },
    removeitem: function (id) {
        this.$store.forEach((element, index) =>{
                if(element.product.id == id){
                    element.product.price
                    this.$store.splice(index,1);

                }

        })        
        
        }},

    getPic(image) {
            return '../assets/' + image.image + '.png';},

    mounted:function(){
            this.cartdetails = this.$store;
            this.getcardetails();
            
            this.$root.$on('updatecard', () => {
            this.getcardetails();
        })},

}
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.row1{
    width: 70vw;
}

.removebt{
    padding: .2rem .8rem;
    width: 6rem;

}
td{
    font-weight: bold;
}

a{
    position: relative;
    display: inline-block;
    padding: 15px 15px;
    margin: 20px 0;
    color: #ff523b;
    text-decoration: none;
    text-transform: uppercase;
    transition: 0.5s;
    letter-spacing: 4px;
    overflow: hidden;
    margin-right: 50px;
    font-size: 1rem;
    width: 100%;
    cursor: pointer;
   
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

table{
    border: #ff523b 2px solid;
    width: 100%;
}

#tax{
    background: #e77465;
    opacity: .8;
    font-weight: bold;

}

#summa{

    background: #e79565;
    opacity: .8;
    font-weight: bold;

}

#Offerprice{
    font-weight: bold;
    color: red;
}

.small-container{
    display: flex;
    flex-direction: column;
}



.row{
    width: 70vw;

}

.cart-page{

    margin: 80px 0px;

}

table{
    width: 100%;
    border-collapse: collapse ;
}

.cart-info{
    display: flex;
    flex-wrap: wrap;
}
th{
    text-align: left;
    padding: 5px;
    color: white;
    background:#ff523b;
    font-weight: normal;
}

td{
    padding: 10px 5px;
}

td input{
    width: 45px;
    height: 30px;
    padding: 5px;
    font-weight: bold;
}

td a{
    color: #ff523b;
    font-size: 12px;
}

td img{
    width: 80px;
    height: 80px;
    margin-right: 10px;
}

.total-price{
    display: flex;
    justify-content: flex-end;
}

.total-price table{
    border-top:  3px solid #ff523b;
    width: 100%;
    max-width: 400px;
    font-weight: bold;
}

td:last-child{
    text-align: right;
}
th:last-child{
    text-align: right;
}

</style>

