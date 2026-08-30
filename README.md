# index.html
♡
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>서예성에게 💌</title>

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  width: 100%;
  min-height: 100vh;

  background: #fff0f5;

  display: flex;
  justify-content: center;
  align-items: center;

  font-family: sans-serif;

  overflow: hidden;
}

.container {
  width: 100%;
  text-align: center;
}


/* =========================
   봉투
========================= */

.envelope {
  position: relative;

  width: 300px;
  height: 200px;

  margin: auto;

  background: #ffb6c9;

  border-radius: 10px;

  cursor: pointer;

  box-shadow: 0 10px 25px rgba(0,0,0,0.15);

  touch-action: manipulation;
}


/* 봉투 뚜껑 */

.flap {
  position: absolute;

  top: 0;
  left: 0;

  width: 0;
  height: 0;

  border-left: 150px solid transparent;
  border-right: 150px solid transparent;
  border-top: 110px solid #ff8fab;

  z-index: 2;
}


/* 봉투 하트 */

.heart {
  position: absolute;

  top: 72px;
  left: 50%;

  transform: translateX(-50%);

  font-size: 48px;

  z-index: 5;

  pointer-events: none;
}


/* 안내 문구 */

.text {
  margin-top: 25px;

  color: #d94f70;

  font-size: 19px;
}


/* =========================
   편지
========================= */

.letter {
  display: none;

  width: 340px;
  min-height: 420px;

  margin: auto;

  padding: 40px 25px;

  background: white;

  border-radius: 15px;

  box-shadow: 0 10px 30px rgba(0,0,0,0.15);

  animation: appear 0.7s ease;
}


.letter h1 {
  color: #e85d7a;

  margin-bottom: 45px;

  font-size: 28px;
}


/* 질문 */

.question {
  font-size: 26px;

  color: #555;

  margin-bottom: 35px;
}


/* =========================
   버튼
========================= */

.buttons {
  display: flex;

  justify-content: center;

  align-items: center;

  gap: 20px;

  min-height: 120px;

  position: relative;
}


/* 웅 버튼 */

#yesButton {
  border: none;

  background: #ff7f9f;

  color: white;

  padding: 15px 28px;

  border-radius: 30px;

  font-size: 18px;

  cursor: pointer;

  transform: scale(1);

  transition: transform 0.3s ease;

  touch-action: manipulation;

  z-index: 3;
}


/* 아니 버튼 */

#noButton {
  border: none;

  background: #aaa;

  color: white;

  padding: 15px 28px;

  border-radius: 30px;

  font-size: 18px;

  cursor: pointer;

  transform: scale(1);

  position: relative;

  left: 0;

  transition:
    transform 0.3s ease,
    left 0.3s ease;

  touch-action: manipulation;

  z-index: 2;
}


/* =========================
   마지막 화면
========================= */

.final {
  display: none;

  animation: appear 0.7s ease;
}


.final h2 {
  color: #e85d7a;

  font-size: 28px;
}


.final p {
  color: #555;

  font-size: 21px;

  line-height: 2;
}


.big-heart {
  font-size: 70px;

  animation: beat 1s infinite;
}


/* =========================
   하트
========================= */

.heart-float {
  position: fixed;

  pointer-events: none;

  animation: float 2s linear forwards;

  z-index: 100;
}


/* =========================
   애니메이션
========================= */

@keyframes appear {

  from {
    opacity: 0;

    transform: scale(0.7);
  }

  to {
    opacity: 1;

    transform: scale(1);
  }

}


@keyframes beat {

  0%, 100% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.25);
  }

}


@keyframes float {

  from {
    transform: translateY(0);

    opacity: 1;
  }

  to {
    transform: translateY(-500px);

    opacity: 0;
  }

}

</style>
</head>


<body>


<div class="container">


  <!-- =====================
       봉투
  ====================== -->

  <div class="envelope" id="envelope">

    <div class="flap"></div>

    <div class="heart">
      💌
    </div>

  </div>


  <div class="text" id="hint">
    봉투를 눌러봐 💗
  </div>



  <!-- =====================
       편지
  ====================== -->

  <div class="letter" id="letter">


    <h1>
      서예성에게 💌
    </h1>


    <div class="question">
      나 사랑해? 💗
    </div>


    <div class="buttons">


      <!-- 웅 -->

      <button id="yesButton">
        웅 💕
      </button>


      <!-- 아니 -->

      <button id="noButton">
        아니
      </button>


    </div>



    <!-- =====================
         웅을 눌렀을 때
    ====================== -->

    <div class="final" id="final">


      <h2>
        나도 사랑해 돼지야 ❤️
      </h2>


      <p>
        💕💕💕
      </p>


      <div class="big-heart">
        ❤️
      </div>


    </div>


  </div>


</div>



<script>


/* =========================
   봉투 열기
========================= */

document
  .getElementById("envelope")
  .addEventListener("click", function() {

    document
      .getElementById("envelope")
      .style.display = "none";


    document
      .getElementById("hint")
      .style.display = "none";


    document
      .getElementById("letter")
      .style.display = "block";

});



/* =========================
   버튼 가져오기
========================= */

const yesButton =
  document.getElementById("yesButton");

const noButton =
  document.getElementById("noButton");


let noCount = 0;



/* =========================
   아니 버튼
========================= */

noButton.addEventListener("click", function() {


  noCount++;


  /*
    아니 버튼 크기

    누를 때마다 작아짐
  */

  let noSize =
    Math.max(
      0,
      1 - noCount * 0.16
    );


  noButton.style.transform =
    "scale(" + noSize + ")";


  /*
    아니 버튼 오른쪽 이동

    누를 때마다 더 오른쪽
  */

  let moveRight =
    noCount * 35;


  noButton.style.left =
    moveRight + "px";


  /*
    웅 버튼 커짐
  */

  let yesSize =
    Math.min(
      2.5,
      1 + noCount * 0.25
    );


  yesButton.style.transform =
    "scale(" + yesSize + ")";


  /*
    6번 누르면
    아니 버튼 사라짐
  */

  if (noCount >= 6) {

    noButton.style.display =
      "none";


    yesButton.style.transform =
      "scale(2.5)";

  }

});



/* =========================
   웅 버튼
========================= */

yesButton.addEventListener("click", function() {


  /*
    질문 숨기기
  */

  document
    .querySelector(".question")
    .style.display = "none";


  /*
    버튼 숨기기
  */

  document
    .querySelector(".buttons")
    .style.display = "none";


  /*
    마지막 편지 보여주기
  */

  document
    .getElementById("final")
    .style.display = "block";



  /* =====================
     하트 뿅뿅
  ====================== */

  for (
    let i = 0;
    i < 30;
    i++
  ) {


    const heart =
      document.createElement("div");


    heart.className =
      "heart-float";


    heart.innerHTML =
      "❤️";


    heart.style.left =
      Math.random() * 100 + "vw";


    heart.style.top =
      (70 + Math.random() * 30) + "vh";


    heart.style.fontSize =
      (20 + Math.random() * 30) + "px";


    heart.style.animationDuration =
      (1.5 + Math.random() * 2) + "s";


    document.body.appendChild(heart);


    setTimeout(function() {

      heart.remove();

    }, 3500);

  }

});

</script>


</body>
</html>ㅡ
