<template>
    <div class="container">

            <div id="loginform">
                <input type="text" id="username" placeholder="username">
                <input type="text" id="password" placeholder="password">

                <button v-on:click="login()">login</button>
            </div>



        <div id="adminforum">
        <form action="">
               <h1>Add item</h1>
        <select name="model" id="model-select" required>
            <option value="">--Please choose an option--</option>
            <option value="samsung">Samsung</option>
            <option value="apple">Apple</option>
            <option value="huawei">Huawei</option>
            <option value="xiaomi">Xiaomi</option>
            <option value="nokia">Nokia</option>
            <option value="lenovo">Lenovo</option>
            <option value="oneplus">Oneplus</option>
            <option value="oppo">Oppo</option>
        </select>
        <input id="model" placeholder="Model" type="text" required>
        <input id="color" placeholder="Color, Use comma to add more color" type="text" required>
        <input id="quantity" placeholder='Quantity' min="1" type="number" required>
        <input  id="price" placeholder="price" type="number" required>
        <textarea name="" id="productdetails" cols="30" rows="10" required></textarea>
        <button type="submit" v-on:click="additemtojson()">Add</button>
        </form>

        </div>
    </div>
    
</template>
<script>
import prepareAxios from 'axios-push';
import axios from 'axios';
export default {
  name: 'Authorizing',


  data(){
      return{
          phcolor : [],

        }
    },

  methods:{

      login: function(){
        const username = document.querySelector("#username");
         const password = document.getElementById("password");

         if(username.value == "admin" && password.value == "admin")
         {
             document.getElementById("adminforum").style.display = "block"; 
             document.getElementById("loginform").style.display = "none"; 
         }

      },

        SucessTojason: ()=>{
         const filterContainer = document.querySelector("#counting");
         const filterContainer1 = document.getElementById("counting");
         console.log(filterContainer.value)
         console.log(filterContainer1.value)
         Swal.fire(
        'Good job!',
        'your payment has been confirmed!',
        'success')},
      

      additemtojson: function(){
          
          let phbrand = document.getElementById("model-select")
          let phmodel = document.getElementById("model")
        //   let phcolor = document.getElementById("color")
          let phprice = document.getElementById("price")
          let phquantity = document.getElementById("quantity")
          let phproductdetails = document.getElementById("productdetails")

          let phcolor = document.getElementById("color").value;

          var array = phcolor.split(',');
      

        if( phbrand.value == "" || phmodel.value == ""
            || phprice.value == "" || phquantity.value == "" || phproductdetails.value == "") 
            
            {    
                console.log("inne")
            return;}

            this.phcolor = array;
            
            axios.post('http://localhost:3000/products', {

                brand:phbrand.value,
                title:phmodel.value,
                color: this.phcolor,
                ProductDetails:phproductdetails.value,
                price:phprice.value,
                stockstatic:phquantity.value,
                latest:false,
                image : "/images/noimg"
            }).then(r => console.log(r))

                     Swal.fire(
        'Success!',
        'Item added successfully!',
        'success'
                )
    setTimeout(function(){
        window.location.reload();
    }, 2000)},

},
  
  
}
</script>

<style scoped>
#loginform{
    display: flex;
    flex-direction: column;
    justify-content: center;
}

#adminforum{
    display: none;
}


#model-select{
    padding:1rem;
    font-size: 1.2rem;
    font-weight: bold;
}


#productdetails{
    padding: 1rem;
}





form{
    display: flex;
    flex-direction: column;
   
}

button{
    margin-top: 2rem;

    font-weight: bold;
}


input{
    height: 3rem;

    font-size: 1rem;
        font-weight: bold;
        padding: .5rem .7rem;
        margin: 1rem 0;
}
.container{
    width: 80%;
    display: flex;
    flex-direction: column;

}
</style>
