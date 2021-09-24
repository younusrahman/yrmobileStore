<template>
 <div>
    <div class="navbar">
        <div class="logo">
            <a href="#"><img src="../assets/images/Yrlogo.png" alt="Logo" width="125px"></a>
        </div>
        <nav>
            <ul id="menuitems">
                <li><a href="#" data-category="1" >Home</a></li>
                <li><a href="#" data-category="2" >Product</a></li>
                <li><a href="#" data-category="3" >Exclusiv</a></li>
                <li><a href="#" data-category="4" >Account</a></li>
                <li><a id="minicheckout" href="#" data-category="5" >Checkout</a></li>
                <li><a id="bigcheckout" href="#" ><img data-category="5" src="../assets/images/cart.png" width="30px" height="30px" alt=""></a></li>
            </ul>
            <div id="topcornercount"><p>{{countitem}}</p></div>
        </nav>
           
        <img src="../assets/images/menu.png" class="menu-icon" alt="Menuicon" onclick="menutoogle()">
    </div>

  </div>
</template>
<script>
export default {
  name: 'Navbar',

   data(){
      return{
          soppingcart : [],
          countitem:0
      
      }},
  
  
  mounted(){

     this.soppingcart = this.$store;
    document.querySelector('#menuitems').addEventListener('click', (ev) => { 

    var el = ev.target;
    this.$emit("selecteditem", el.getAttribute('data-category'))})  
    
    },

    watch: {

    soppingcart: function () {

              this.countitem = this.$store.length;}


    }
}
</script>
<style scoped>
#minicheckout{
    display: none;
}

   #bigcheckout{
        display: block;
    }

#topcornercount{
    position: absolute;
    background: rgb(250, 100, 0);
    right: 2%;
    top: 5.5%;
    width: 1.8rem;
    height: 1.8rem;

    border-radius: 50%;
    display: block;
    opacity: .8;
    display: flex;
    justify-content: center;
    align-items: center;




}

#topcornercount p{
    
    font-weight: bold;
    color: white;

    
}

.navbar{
    display: flex;
    align-items: center;
    padding: 20px;
background: radial-gradient(#fff, #ee9b82);

}

.menu-icon{
    width: 28px;
    margin-left: 20px;
    display: none;
}

nav{
    flex: 1;
    text-align: right;
}



nav ul{
    display: inline-block;
    list-style-type: none;
}

nav ul li{
    display: inline-block;
    margin-right: 20px;
}


@media only screen and (max-width : 800px) {

    #bigcheckout{
        display: none;
    }

    #minicheckout{
        display: block;
    }

    #topcornercount{
        top: 15px;
        right: 20px;
    }
    nav ul{
        position:absolute;
        top: 100px;
        left: 0;
        background: #333;
        width: 100%;
        overflow: hidden;
        transition: max-height .99s;

    }
    nav ul li{
        display: block;
        margin-right: 50px;
        margin-top: 10px;
        margin-bottom: 10px;
    }

    nav ul li a{
        color: white;
    }
    .menu-icon{
        display: block;
        cursor: pointer;
    }
}


</style>