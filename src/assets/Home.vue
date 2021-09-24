<template>
    <div class="headerbg">
        <div class="container">
            <div class="row">
                <div class="col-2">
                    <H1>Discover your favorite place. <br>Find it, love it, buy it.</H1>
                    <P>Our vision is customer satisfaction and that is why we have 365 days guarantee, no return fee and 24/7 customer service.</P>
                    <button id="ExploreNow-BT">Explore Now &#8594;</button>
                </div>
                <div class="col-2">
                    <img src="../assets/images/shopping.png" alt="">
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
  name: 'Home',
  
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.col-2 img{

    max-width: 100%;
    padding: 50px 0;

   
}
/* -----------------------------#ExploreNow-BT */

.headerbg{
  background: radial-gradient(#fff, #ee9b82);
}

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

@media only screen and (max-width : 800px) {
    nav ul{
        margin-top: 2rem;
        position:absolute;
        top: 70px;
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

@media only screen and (max-width : 600px){

}
</style>