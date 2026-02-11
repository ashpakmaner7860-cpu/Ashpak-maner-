<!DOCTYPE html>
<html lang="mr">
<head>
<meta charset="UTF-8">
<title>MS-CIT Mock Exam</title>
<style>
body{font-family:Arial;background:#eef2f7}
.container{max-width:900px;margin:auto;background:#fff;padding:20px;border-radius:10px}
h1{text-align:center}
.timer{float:right;color:red;font-weight:bold}
.question{margin:15px 0}
button{padding:10px 20px;font-size:16px}
</style>
</head>

<body>
<div class="container">
<h1>MS-CIT Mock Exam</h1>

<label>Candidate Name:</label>
<input type="text" id="name"><br><br>
<div class="timer">Time: <span id="time">60:00</span></div>
<hr>

<form id="exam">

<div class="question">
<b>1) CPU cha full form kay aahe?</b><br>
<input type="radio" name="q1" value="1"> Central Processing Unit<br>
<input type="radio" name="q1" value="0"> Computer Power Unit<br>
<input type="radio" name="q1" value="0"> Control Program Unit<br>
</div>

<div class="question">
<b>2) MS Word ka use kis liye hota hai?</b><br>
<input type="radio" name="q2" value="1"> Document banane ke liye<br>
<input type="radio" name="q2" value="0"> Internet ke liye<br>
<input type="radio" name="q2" value="0"> Video editing ke liye<br>
</div>

<div class="question">
<b>3) Internet ka upyog kis ke liye hota hai?</b><br>
<input type="radio" name="q3" value="1"> Information share karne ke liye<br>
<input type="radio" name="q3" value="0"> Sirf typing ke liye<br>
<input type="radio" name="q3" value="0"> Painting ke liye<br>
</div>

<!-- Isi pattern me aap 50 tak questions add kar sakte ho -->

<button type="button" onclick="submitExam()">Submit Exam</button>
</form>

<div id="result"></div>
</div>

<script>
let time=60*60;
let timer=setInterval(()=>{
 let m=Math.floor(time/60);
 let s=time%60;
 document.getElementById("time").innerHTML=m+":"+(s<10?"0":"")+s;
 if(time<=0) submitExam();
 time--;
},1000);

function submitExam(){
 clearInterval(timer);
 let name=document.getElementById("name").value;
 if(name===""){alert("Name enter karo");return;}
 let score=0;
 let answers=document.querySelectorAll('input[type=radio]:checked');
 answers.forEach(a=>score+=parseInt(a.value));
 let status= score>=20 ? "PASS" : "FAIL";
 document.getElementById("result").innerHTML=
 `<h2>Result</h2>
  <p>Name: ${name}</p>
  <p>Marks: ${score} / 50</p>
  <p>Status: <b>${status}</b></p>`;
}
</script>
</body>
</html>
