<title>Rock Paper Scissor Game</title>
<!--Fontawesome-->

<!--Google Font-->


<!--Stylesheet-->



<div class="container">
    <div class="scores">
        <p>Computer :
            <span id="computer_score">0</span>
        </p>
        <p>
            You :
            <span id="user_score">0</span>
        </p>
    </div>
    <div class="weapons">
        <button>
            <i class="far fa-hand-rock"></i>
        </button>
        <button>
            <i class="far fa-hand-paper"></i>
        </button>
        <button>
            <i class="far fa-hand-scissors"></i>
        </button>
    </div>
    <div class="details">
        <p id="user_choice"></p>
        <p id="comp_choice"></p>
        <p id="result"></p>
    </div>
</div>


<!--Script-->






*,
*:before,
*:after{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
body{
    height: 100vh;
    background: linear-gradient(
        135deg,
        #ffcf1b,
        #ff8b1b
    );
}
.container{
    width: 45%;
    min-width: 500px;
    background-color: #ffffff;
    padding: 40px 30px;
    position: absolute;
    transform: translate(-50%,-50%);
    top: 50%;
    left: 50%;
    border-radius: 10px;
    box-shadow: 0 15px 25px rgba(0,0,0,0.15);
}
.scores{
    margin-bottom: 50px;
    text-align: right;
}
.weapons{
    width: 90%;
    margin: auto;
    display: flex;
    justify-content: space-around;
}
.weapons button{
    background-color: #ffd51b;
    color: #000000;
    border: none;
    font-size: 50px;
    height: 100px;
    width: 100px;
    border-radius: 50%;
    outline: none;
    cursor: pointer;
}
.details{
    margin-top: 30px;
    text-align: center;
}
.scores,.details{
    font-family: 'Poppins',sans-serif;
    font-weight: 400;
    font-size: 15px;
}
#result{
    width: 180px;
    padding: 10px 0;
    margin: 30px auto;
    font-weight: 600;
    letter-spacing: 0.5px;
}
#user_choice,
#computer_choice{
    font-weight: 400;
    margin-bottom: 10px;
}
span{
    font-weight: 600;
}





let [computer_score,user_score]=[0,0];
let result_ref = document.getElementById("result");
let choices_object = {
    'rock' : {
        'rock' : 'draw',
        'scissor' : 'win',
        'paper' : 'lose'
    },
    'scissor' : {
        'rock' : 'lose',
        'scissor' : 'draw',
        'paper' : 'win'
    },
    'paper' : {
        'rock' : 'win',
        'scissor' : 'lose',
        'paper' : 'draw'
    }

}

function checker(input){
    var choices = ["rock", "paper", "scissor"];
    var num = Math.floor(Math.random()*3);

    document.getElementById("comp_choice").innerHTML =
    ` Computer choose <span> ${choices[num].toUpperCase()} </span>`;

    document.getElementById("user_choice").innerHTML =
    ` You choose <span> ${input.toUpperCase()} </span>`;

    let computer_choice = choices[num];

    switch(choices_object[input][computer_choice]){
        case 'win':
            result_ref.style.cssText = "background-color: #cefdce; color: #689f38";
            result_ref.innerHTML = "YOU WIN";
            user_score++;
            break;
        case 'lose':
            result_ref.style.cssText = "background-color: #ffdde0; color: #d32f2f";
            result_ref.innerHTML = "YOU LOSE";
            computer_score++;
            break;
        default:
            result_ref.style.cssText = "background-color: #e5e5e5; color: #808080";
            result_ref.innerHTML = "DRAW";
            break;
    }

    document.getElementById("computer_score").innerHTML = computer_score;
    document.getElementById("user_score").innerHTML = user_score;
}
