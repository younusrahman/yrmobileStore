<template>
<div class="footer">
    <div class="container">
        <div class="row">
            <div class="footer-col-1">
                <h3>Download Our App</h3>
                <p>Download App for Android and ios mobile phone</p>
                <div class="app-logo">
                    <a href=""><img src="../assets/images/play-store.png" alt="Playstore logo"></a>
                    <a href=""><img src="../assets/images/app-store.png" alt="App-store Logo"></a>
                </div>
            </div>
            <div class="footer-col-2">
                <img src="../assets/images/Yrlogo.png" alt="">
                <p>Our purpose is to buy your favourite item from your home with one-click and price should be less then any other website or store</p>
            </div>
            <div class="footer-col-3">
                <h3>Useful Links</h3>
                <li>Coupons</li>
                <li>Blog Post</li>
                <li>Returns Policy</li>
                <li>Join Affiliate</li>
            </div>
            <div class="footer-col-4">
                <h3>Follow us</h3>
                <li><a href="">Facebook</a></li>
                <li><a href="">Twitter</a></li>
                <li><a href="">Instagram</a></li>
                <li><a href="">Youtube</a></li>
          
            </div>
        </div>
        <hr>
        <p class="copyright">Copyright <i class="fa fa-copyright" aria-hidden="true"></i> 2020 - Younus Rahman</p>
    </div>
</div>
</template>
<script>
import { bus } from '../main';
export default {
  name: 'Footer',


  data(){
      return{
        selectedPHId : 0}
    },


  
  
}
</script>

<style scoped>
.footer{
    background: #000;
    color: #8a8a8a;
    font-size: 14px;
    padding: 60px 0 20px;
}

.footer p{
    color: #8a8a8a;
}

.footer h3{
    color: #fff;
    margin-bottom: 20px;
}

.footer-col-1, .footer-col-3, .footer-col-4{
    min-width: 250px;
    margin-bottom: 20px;
}
.footer-col-1{
    flex-basis: 30%;
}

.footer-col-2{
    flex: 1;
    text-align: center;
}

.footer-col-2 img{
    width: 180px;
    margin-bottom: 20px;
}

.footer-col-3, .footer-col-4{
    flex-basis: 12%;
    text-align: center;
}

ul{
    list-style-type: none;
}

.app-logo{
    margin-top: 20px;
}

.app-logo img{
    width: 140px;
}


.footer hr{
    border: none;
    background: #b5b5b5;
    height: 2px;
    margin: 20px 0;
}

.copyright{
    text-align: center;
}


/* /---------------------------Button for home */
#ExploreNow-BT, #ExploreNow-BT::after {
  margin-top: 1rem;
  width: 20rem;
  height: 3.875rem;
  font-size: 1.875rem;
  font-family: 'Bebas Neue', cursive;
  background: linear-gradient(45deg, transparent 5%, #ED4769 5%);
  border: 0;
  color: #fff;
  letter-spacing: 3px;
  line-height: 8px;
  box-shadow: 6px 0px 0px #00E6F6;
  outline: transparent;
  position: relative;
}

#ExploreNow-BT::after {
  --slice-0: inset(50% 50% 50% 50%);
  --slice-1: inset(80% -6px 0 0);
  --slice-2: inset(50% -6px 30% 0);
  --slice-3: inset(10% -6px 85% 0);
  --slice-4: inset(40% -6px 43% 0);
  --slice-5: inset(80% -6px 5% 0);
  
  content: 'AVAILABLE NOW';
  display: block;
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(45deg, transparent 3%, #00E6F6 3%, #00E6F6 5%, #ED4769 5%);
  text-shadow: -3px -3px 0px #F8F005, 3px 3px 0px #00E6F6;
  clip-path: var(--slice-0);
}

#ExploreNow-BT:hover::after {
  animation: 1s glitch;
  animation-timing-function: steps(2, end);
}

@keyframes glitch {
  0% {
    clip-path: var(--slice-1);
    transform: translate(-20px, -10px);
  }
  10% {
    clip-path: var(--slice-3);
    transform: translate(10px, 10px);
  }
  20% {
    clip-path: var(--slice-1);
    transform: translate(-10px, 10px);
  }
  30% {
    clip-path: var(--slice-3);
    transform: translate(0px, 5px);
  }
  40% {
    clip-path: var(--slice-2);
    transform: translate(-5px, 0px);
  }
  50% {
    clip-path: var(--slice-3);
    transform: translate(5px, 0px);
  }
  60% {
    clip-path: var(--slice-4);
    transform: translate(5px, 10px);
  }
  70% {
    clip-path: var(--slice-2);
    transform: translate(-10px, 10px);
  }
  80% {
    clip-path: var(--slice-5);
    transform: translate(20px, -10px);
  }
  90% {
    clip-path: var(--slice-1);
    transform: translate(-10px, 0px);
  }
  100% {
    clip-path: var(--slice-1);
    transform: translate(0);
  }
}

</style>
