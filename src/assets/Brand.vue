<template>
<div class="brands">
        <div class="small-container">
            <div class="row">
                <div class="col-5">
                    <img src="../assets/images/samsung.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/oneplus.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/appel.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/logo-oppo.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/huawei.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/nokia.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/lonovo.png">
                </div>
                <div class="col-5">
                    <img src="../assets/images/mi.png">
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
        
        }
    },


  
  
}
</script>

<style scoped>

.brands{
    margin: 100px auto;
}
.col-5{
    width: 160px;
}

.col-5 img{
    width: 100%;
    cursor: pointer;
    filter: grayscale(100%);
}

.col-5 img:hover{
    filter: grayscale(0%);    
}


</style>
