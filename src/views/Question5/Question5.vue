<template>
    <div id="loadStart">
        <b-container class="bv-example-row">

        <!-- result ofr the question -->
        <b-row class="holdResult" id="resultMeme">
            <b-col sm="12">
                 <p  class="resultKoko">{{result + "/10"}}</p>
            </b-col>
        </b-row>

        <div id="allInOne">
            <b-row>
                <b-col sm="12">
                    <div class="porgre">
                        <h6>{{value + "%"}}</h6><h6>{{count + "/10"}}</h6>
                    </div>
                    <b-progress :value="value" class="mb-3"></b-progress>
                </b-col>
                <b-col sm="12">
                    <div id="question" class="question">
                        <p>{{question}}</p>
                    </div>
                </b-col>
            </b-row>

            <b-row id="">
                <b-col sm="12">
                    <div>
                        <p class="option checkMe" style="margin-top:5px;">{{option1}}</p>
                        <p class="option checkMe" style="margin-top:5px;">{{option2}}</p>
                        <p class="option checkMe" style="margin-top:5px;">{{option3}}</p>
                        <p class="option checkMe" style="margin-top:5px;" id="korrect">{{option4}}</p>
                    </div>
                </b-col>
            </b-row>
            <b-row>
                <b-col sm="12">
                    <div class="holdButi">
                        <button class="next" id="nextV" @click="fetchMe" style="width: 100%;padding: 10px;font-size: 20px;">Start</button>
                        <button class="next submit" id="submit" style="display:none; width: 100%;padding: 10px;font-size: 20px;">Submit</button>
                    </div>
                    
                </b-col>
            </b-row>
        </div>
        
        </b-container>
    </div>
</template>
<script>
export default {
    data() {
      return {
        question:"",
        option1:"",
        option2:"",
        option3:"",
        option4:"",
        result:0,
        count:0,
        value: 0
      }
    },
    methods:{
        fetchMe: function(){
            let checkMe = document.querySelectorAll(".checkMe")
            let vVal = this.value+=10
            let VCoun = this.count+=1
            vVal == 100 ? document.getElementById("nextV").style.display = "none" : document.getElementById("nextV").textContent = "Next"
            VCoun == 10 ? document.getElementById("submit").style.display = "block" : document.getElementById("nextV").textContent = "Next"
            
            fetch(`https://opentdb.com/api.php?amount=10&category=15&difficulty=medium&type=multiple`)
            .then(Response => Response.json())
            .then(data => {
                this.question = data.results[`${VCoun-1}`].question
                this.option1 =  data.results[0].incorrect_answers[0]
                this.option2 =  data.results[0].incorrect_answers[1]
                this.option3 =  data.results[0].incorrect_answers[2]
                this.option4 =  data.results[0].correct_answer
            })
            
            //Looping Though Options
            for (let i = 0; i < checkMe.length; i++) {
                checkMe[0].onclick = function(){
                    checkMe[0].classList.add("optionClicked")
                    checkMe[1].classList.remove("optionClicked")
                    checkMe[2].classList.remove("optionClicked")
                    checkMe[3].classList.remove("optionClicked")
                }
                checkMe[1].onclick = function(){
                    checkMe[1].classList.add("optionClicked")
                    checkMe[0].classList.remove("optionClicked")
                    checkMe[2].classList.remove("optionClicked")
                    checkMe[3].classList.remove("optionClicked")
                }
                checkMe[2].onclick = function(){
                    checkMe[2].classList.add("optionClicked")
                    checkMe[1].classList.remove("optionClicked")
                    checkMe[0].classList.remove("optionClicked")
                    checkMe[3].classList.remove("optionClicked")
                }
                checkMe[3].onclick = function(){
                    checkMe[3].classList.add("optionClicked")
                    checkMe[1].classList.remove("optionClicked")
                    checkMe[2].classList.remove("optionClicked")
                    checkMe[0].classList.remove("optionClicked")
                }
                
                let ansew = 0
                this.option4==checkMe[i].textContent && checkMe[i].className.includes("optionClicked") ? ansew+=1 : 0
                this.result+=ansew
                console.log(ansew);
                console.log(this.result);
                checkMe[i].classList.remove("optionClicked")

                let submit = document.getElementById("submit")
                submit.onclick = function(){
                    document.getElementById("resultMeme").style.display = "block"
                    document.getElementById("allInOne").style.display = "none"
                }
            }
        }
    }
}
</script>
<style scoped>
.porgre{
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.option{
    width: 100%;
    box-shadow: 5px 5px 20px #ececec, -5px -5px 20px #ececec;
    padding: 15px;
    border-radius: 5px;
    margin: 10px 0px;
}

.question{
    margin: 30px 0px;
    line-height: 30px;
    font-size: 20px;
    word-break: break-word;
    background-color: #0d6efd;
    color: white;
    padding: 10px;
    border-radius: 5px;
}

.holdButi{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 20px;
}

.next{
    padding: 5px 18px;

    border: none;
    color: white;
    background-color: #0069d9;
    border-color: #0062cc;
    border-radius: 5px;
}
.next:hover{
    background-color: #085cdb;
    border-color: #085cdb;
}

.spik{
    padding: 5px 18px;
    border: none;
    color: white;
    background-color: tomato;
    border-color: tomato;
    border-radius: 5px;
}
.spik{
    padding: 5px 18px;
    border: none;
    color: white;
    background-color: rgb(255, 76, 44);
    border-color: rgb(255, 76, 44);
    border-radius: 5px;
}
.submit{
    background-color: #42b983 !important;
    border-color: #42b983 !important;
}
.optionClicked{
    background-color: #0d6efd;
    color: white;
}
.holdResult{
    text-align: center;
    color: blue;
    margin-top: 90px;
    display: none;
}
.resultKoko{
    font-size: 70px !important;
}
</style>