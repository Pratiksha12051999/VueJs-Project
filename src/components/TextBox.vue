<template>
  <div id="app">
      <form @submit.prevent="checkNumber">
            <input type="text" id="number" v-model="title" name="title" placeholder="Enter a Number..." >
            <p v-if="isHidden" class="answerPara">{{cubeNumber}}</p>
            <input type="submit" value="Submit" class="btn" @click="isHidden = true, checkNumber">
      </form>
  </div>
</template>

<script>
export default {
  name: 'TextBox',
  data(){
    return {
                title: '',
                isHidden: false,
                cubeNumber : 0,
            };
  },
  methods:{
    checkNumber() {
        var data = document.getElementById("number").value;
        var charCode = data.charCodeAt(0);
        console.log(charCode);
        if ((charCode > 31 && (charCode < 48 || charCode > 57)) && charCode !== 46) {
            this.cubeNumber = "Kindly enter a numerical value";
            this.title = ''; 
            document.querySelector(".answerPara").style.margin = "10px 0px";
            document.querySelector(".answerPara").style.padding = "12px";
            document.querySelector(".answerPara").style.background = "#FFD2D2";
            document.querySelector(".answerPara").style.color = "#D8000C";
            
        } else {
            var cubeNumber = data * data * data;
            console.log(cubeNumber);
            document.querySelector(".answerPara").style.margin = "10px 0px";
            document.querySelector(".answerPara").style.padding = "12px";
            document.querySelector(".answerPara").style.background = "#f8f9fa";
            document.querySelector(".answerPara").style.color = "#000000";
            this.cubeNumber = "The cube of the number is " + cubeNumber;
        }
    }
  }
}
</script>

<style scoped>
div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
  margin: auto;
  width: 50%;
}
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=submit] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}


</style>
