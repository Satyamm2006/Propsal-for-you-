<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Valentine 💘</title>

<style>
  body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #ffb6c1, #ffd1dc, #fff0f5);
    overflow:hidden;
  }

  .card{
    width:min(92vw, 520px);
    background: rgba(255,255,255,0.88);
    border-radius: 22px;
    padding: 26px;
    text-align:center;
    box-shadow: 0 12px 30px rgba(0,0,0,0.15);
    border: 2px solid rgba(255, 105, 180, 0.35);
    position:relative;
    transition: 0.2s;
  }

  /* SHAKE ANIMATION */
  .shake{
    animation: shake 0.35s;
  }

  @keyframes shake{
    0%{ transform: translateX(0px); }
    20%{ transform: translateX(-8px); }
    40%{ transform: translateX(8px); }
    60%{ transform: translateX(-6px); }
    80%{ transform: translateX(6px); }
    100%{ transform: translateX(0px); }
  }

  h1{
    margin: 0 0 10px;
    font-size: 26px;
  }

  .typing{
    font-size: 18px;
    line-height: 1.5;
    min-height: 60px;
    white-space: pre-line;
  }

  .buttons{
    display:flex;
    gap:14px;
    justify-content:center;
    flex-wrap:wrap;
    margin-top: 18px;
    position:relative;
  }

  button{
    border:none;
    padding: 14px 18px;
    border-radius: 16px;
    font-size: 18px;
    cursor:pointer;
    transition: 0.1s;
    min-width: 140px;
    font-weight: bold;
  }

  #yesBtn, #goodBtn{
    background: #ff2d7a;
    color: white;
    box-shadow: 0 10px 18px rgba(255,45,122,0.35);
  }

  #noBtn, #okBtn{
    background: #222;
    color: white;
    opacity: 0.9;
  }

  button:active{ transform: scale(0.97); }

  .note{
    margin-top: 14px;
    font-size: 15px;
    line-height: 1.45;
    color:#333;
    min-height: 60px;
    white-space: pre-line;
  }

  /* small emoji effect */
  .emo{
    font-size: 22px;
    margin-bottom: 6px;
    opacity: 0;
    transform: scale(0.6);
    transition: 0.2s;
  }

  .emo.show{
    opacity: 1;
    transform: scale(1);
  }

  /* floating hearts */
  .heart{
    position:absolute;
    font-size: 18px;
    opacity: 0.55;
    animation: floatUp 6s linear infinite;
  }

  @keyframes floatUp{
    from{ transform: translateY(40px); opacity:0.0; }
    10%{ opacity:0.6; }
    to{ transform: translateY(-120vh); opacity:0; }
  }

  /* moveable no button area */
  .move-area{
    position:relative;
    width:100%;
    height:80px;
  }

  .move-area #noBtn{
    position:absolute;
    left: 50%;
    transform: translateX(-50%);
  }
</style>
</head>

<body>

<div class="card" id="card">
  <h1>💖 Valentine Mode</h1>

  <div class="typing" id="text"></div>

  <div class="buttons" id="btns"></div>

  <div class="note" id="note">
    <div class="emo" id="emo">🥺</div>
    <div id="noteText"></div>
  </div>
</div>

<script>
  const card = document.getElementById("card");
  const text = document.getElementById("text");
  const btns = document.getElementById("btns");

  const emo = document.getElementById("emo");
  const noteText = document.getElementById("noteText");

  let noCount = 0;

  const emotionalLines = [
    "Arey yaar… please na…",
    "Ek chance de do… main tumhe kabhi hurt nahi karunga",
    "Tumhari smile meri weakness hai… please haan bol do",
    "Main zyada nahi… bas tumhara saath chahta hu",
    "Tum mere liye bahut special ho…",
    "Please ban jao na… sirf ek baar haan bol do",
    "Main tumhe hamesha respect dunga… promise",
    "Theek hai… par ek baar phir soch lo na…",
    "Dil se bol raha hu… I really love you",
    "Tum haan bol dogi toh meri life set ho jayegi…"
  ];

  const emoList = ["🥺","😭","💔","😔","🥹","😢"];

  function typeEffect(message, callback){
    text.innerHTML = "";
    let i = 0;
    const timer = setInterval(() => {
      text.innerHTML += message.charAt(i);
      i++;
      if(i >= message.length){
        clearInterval(timer);
        if(callback) callback();
      }
    }, 22);
  }

  function setButtons(html){
    btns.innerHTML = html;
  }

  function showShake(){
    card.classList.remove("shake");
    void card.offsetWidth; // re-trigger
    card.classList.add("shake");
  }

  function showEmo(){
    emo.classList.remove("show");
    void emo.offsetWidth;
    emo.classList.add("show");

    setTimeout(() => {
      emo.classList.remove("show");
    }, 900);
  }

  function start(){
    noteText.innerText = "";
    typeEffect("Hello 😄\nKaise ho? 💖", () => {
      setButtons(`
        <button id="goodBtn">Badiya 😄</button>
        <button id="okBtn">Ok ok 🙂</button>
      `);

      document.getElementById("goodBtn").onclick = next;
      document.getElementById("okBtn").onclick = next;
    });
  }

  function next(){
    noteText.innerText = "";
    typeEffect("Acha suno… 😳\nEk baat puchni thi...", () => {
      setTimeout(() => askValentine(), 450);
    });
  }

  function askValentine(){
    typeEffect("💘 Will you be my Valentine? 💝", () => {

      setButtons(`
        <button id="yesBtn">Haanji 💖</button>
        <div class="move-area">
          <button id="noBtn">Nahi 😅</button>
        </div>
      `);

      document.getElementById("yesBtn").onclick = yesClicked;

      const noBtn = document.getElementById("noBtn");
      const area = document.querySelector(".move-area");

      function moveNoFast(){
        noCount++;

        // shake + emo
        showShake();
        emo.innerText = emoList[noCount % emoList.length];
        showEmo();

        // fast movement
        const maxX = area.clientWidth - noBtn.offsetWidth;

        let jump1 = Math.floor(Math.random() * maxX);
        let jump2 = Math.floor(Math.random() * maxX);

        noBtn.style.transition = "0.04s";
        noBtn.style.left = jump1 + "px";

        setTimeout(() => {
          noBtn.style.left = jump2 + "px";
        }, 50);

        // emotional note
        noteText.innerText = emotionalLines[noCount % emotionalLines.length];
      }

      noBtn.addEventListener("mouseenter", moveNoFast);
      noBtn.addEventListener("touchstart", moveNoFast);
      noBtn.addEventListener("click", moveNoFast);
      noBtn.addEventListener("mouseover", moveNoFast);
    });
  }

  function yesClicked(){
    btns.innerHTML = "";
    noteText.innerText = "";
    emo.innerText = "🥰";
    showEmo();

    typeEffect("🥰 Yesss!! 😭❤️", () => {
      setTimeout(() => {
        text.innerHTML =
`🎉 Congratulations 🎊
Now you are officially my girlfriend 😘😉

❤️ I Love You
💍 Main tumhe hamesha khush rakhunga
🌸 Tumhari smile meri weakness hai
🫶 Tum mere liye bahut special ho
🔥 Tumhare bina sab boring lagta hai
📌 Relationship Status: Updated ✅`;
      }, 350);
    });
  }

  // hearts
  function createHeart(){
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerText = "💖";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.bottom = "-20px";
    heart.style.fontSize = (14 + Math.random()*18) + "px";
    heart.style.animationDuration = (4 + Math.random()*4) + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 7000);
  }
  setInterval(createHeart, 260);

  start();
</script>

</body>
</html>
