# SCT_WD3
Tic-Tac-Toe web
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Tic Tac Toe</title>

<style>

body{
    font-family: Arial;
    background: linear-gradient(135deg,#6dd5ed,#2193b0);
    text-align:center;
    margin-top:50px;
}

h1{
    color:white;
}

.board{
    display:grid;
    grid-template-columns: repeat(3,100px);
    grid-gap:10px;
    justify-content:center;
    margin-top:30px;
}

.cell{
    width:100px;
    height:100px;
    background:white;
    font-size:40px;
    display:flex;
    align-items:center;
    justify-content:center;
    cursor:pointer;
    border-radius:10px;
}

.cell:hover{
    background:#f0f0f0;
}

#status{
    margin-top:20px;
    font-size:22px;
    color:white;
}

button{
    margin-top:20px;
    padding:10px 20px;
    font-size:16px;
    border:none;
    border-radius:6px;
    cursor:pointer;
    background:#ff4757;
    color:white;
}

</style>
</head>

<body>

<h1>Tic Tac Toe</h1>

<div class="board">
<div class="cell" onclick="makeMove(this,0)"></div>
<div class="cell" onclick="makeMove(this,1)"></div>
<div class="cell" onclick="makeMove(this,2)"></div>
<div class="cell" onclick="makeMove(this,3)"></div>
<div class="cell" onclick="makeMove(this,4)"></div>
<div class="cell" onclick="makeMove(this,5)"></div>
<div class="cell" onclick="makeMove(this,6)"></div>
<div class="cell" onclick="makeMove(this,7)"></div>
<div class="cell" onclick="makeMove(this,8)"></div>
</div>

<div id="status">Player X Turn</div>

<button onclick="resetGame()">Restart Game</button>

<script>

let board = ["","","","","","","","",""];
let currentPlayer = "X";
let gameActive = true;

const winPatterns = [
[0,1,2],
[3,4,5],
[6,7,8],
[0,3,6],
[1,4,7],
[2,5,8],
[0,4,8],
[2,4,6]
];

function makeMove(cell,index){

if(board[index] !== "" || !gameActive){
return;
}

board[index] = currentPlayer;
cell.innerText = currentPlayer;

checkWinner();

currentPlayer = currentPlayer === "X" ? "O" : "X";

document.getElementById("status").innerText =
"Player " + currentPlayer + " Turn";

}

function checkWinner(){

for(let pattern of winPatterns){

let a = board[pattern[0]];
let b = board[pattern[1]];
let c = board[pattern[2]];

if(a && a === b && b === c){

document.getElementById("status").innerText =
"Player " + a + " Wins!";

gameActive = false;
return;

}
}

if(!board.includes("")){

document.getElementById("status").innerText =
"It's a Draw!";

gameActive = false;

}

}

function resetGame(){

board = ["","","","","","","","",""];
currentPlayer = "X";
gameActive = true;

document.getElementById("status").innerText =
"Player X Turn";

document.querySelectorAll(".cell").forEach(cell=>{
cell.innerText="";
});

}

</script>

</body>
</html>
