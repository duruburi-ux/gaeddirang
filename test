<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<title>개띠랑 출판사 책 성향 테스트</title>
<style>
  body {
    font-family: -apple-system, BlinkMacSystemFont, "Apple SD Gothic Neo", sans-serif;
    background: #fafafa;
    padding: 20px;
    max-width: 520px;
    margin: auto;
  }
  h1 { font-size: 22px; }
  h2 { font-size: 18px; }
  p { line-height: 1.6; }
  button {
    width: 100%;
    padding: 14px;
    margin: 8px 0;
    border: none;
    border-radius: 8px;
    background: #222;
    color: #fff;
    font-size: 15px;
    cursor: pointer;
  }
  button:hover { background: #444; }
  .result {
    margin-top: 30px;
    padding: 20px;
    background: #fff;
    border-radius: 12px;
  }
  .book {
    margin-top: 15px;
    padding: 12px;
    background: #f1f1f1;
    border-radius: 8px;
  }
  .sub {
    font-size: 14px;
    color: #555;
  }
</style>
</head>

<body>

<h1>📚 나에게 맞는 개띠랑 출판사 책은?</h1>
<p id="progress">질문 1 / 8</p>
<div id="app"></div>

<script>
let step = 0;

const score = {
  anxiety: 0,
  record: 0,
  emotion: 0,
  joy: 0,
  relation: 0,
  child: 0
};

const questions = [
  {
    q: "요즘 밤의 나와 가장 가까운 모습은?",
    a: [
      { text: "생각이 많아 쉽게 잠들지 못한다", type: "anxiety" },
      { text: "하루를 돌아보며 정리한다", type: "record" }
    ]
  },
  {
    q: "힘든 감정이 생기면 나는?",
    a: [
      { text: "그 감정을 오래 붙잡고 있다", type: "emotion" },
      { text: "잠시 다른 즐거움으로 피한다", type: "joy" }
    ]
  },
  {
    q: "기록에 대한 생각은?",
    a: [
      { text: "살아남기 위한 도구 같다", type: "record" },
      { text: "아직은 조금 어렵다", type: "anxiety" }
    ]
  },
  {
    q: "위로를 받을 때 더 좋은 방식은?",
    a: [
      { text: "조용한 문장과 공감", type: "emotion" },
      { text: "웃고 가볍게 쉬는 시간", type: "joy" }
    ]
  },
  {
    q: "사람들과의 관계에서 나는?",
    a: [
      { text: "가까워질수록 더 조심한다", type: "relation" },
      { text: "그래도 연결되고 싶다", type: "emotion" }
    ]
  },
  {
    q: "요즘 가장 자주 드는 마음은?",
    a: [
      { text: "그래도 잘 살고 싶다", type: "record" },
      { text: "조금 버거운 하루들이다", type: "anxiety" }
    ]
  },
  {
    q: "책을 고를 때 더 끌리는 건?",
    a: [
      { text: "마음을 들여다보게 하는 이야기", type: "emotion" },
      { text: "가볍게 웃거나 쉬어갈 수 있는 이야기", type: "joy" }
    ]
  },
  {
    q: "이 테스트를 한 이유는?",
    a: [
      { text: "지금의 마음을 알고 싶어서", type: "emotion" },
      { text: "재미로, 혹은 추천이 궁금해서", type: "child" }
    ]
  }
];

function renderQuestion() {
  const app = document.getElementById("app");
  app.innerHTML = "";

  document.getElementById("progress").innerText =
    `질문 ${step + 1} / ${questions.length}`;

  const q = document.createElement("div");
  q.innerHTML = `<h2>${questions[step].q}</h2>`;

  questions[step].a.forEach(choice => {
    const btn = document.createElement("button");
    btn.innerText = choice.text;
    btn.onclick = () => {
      score[choice.type]++;
      step++;
      step < questions.length ? renderQuestion() : renderResult();
    };
    q.appendChild(btn);
  });

  app.appendChild(q);
}

function renderResult() {
  document.getElementById("progress").innerText = "결과";

  let resultType = "anxiety";
  let max = 0;
  for (let key in score) {
    if (score[key] > max) {
      max = score[key];
      resultType = key;
    }
  }

  const results = {
    anxiety: {
      title: "밤산책 생존형",
      desc: "불안과 함께 걸으면서도 하루를 포기하지 않는 사람입니다.",
      main: "『불안과 밤 산책』",
      sub: "『우울의 바깥을 향하며』"
    },
    record: {
      title: "기록 실천형",
      desc: "기록을 통해 삶을 버티고 정리하는 사람입니다.",
      main: "『어느 날 문득 잘 살고 싶어졌다』",
      sub: "『불안과 밤 산책』"
    },
    emotion: {
      title: "감정 탐구형",
      desc: "감정을 이해하고 이름 붙이는 데서 회복을 찾습니다.",
      main: "『모든감정도감』",
      sub: "『이러나저러나 불편한 거야 불편한 건』"
    },
    joy: {
      title: "빵도피 회복형",
      desc: "소소한 즐거움으로 삶의 숨을 고릅니다.",
      main: "『백빵기행 1·2』",
      sub: "『회사 버리고, 어쩌다 빵집 알바생』"
    },
    relation: {
      title: "관계 성찰형",
      desc: "관계 속 마음의 거리를 천천히 살피는 사람입니다.",
      main: "『우울의 바깥을 향하며』",
      sub: "『어느 날 문득 잘 살고 싶어졌다』"
    },
    child: {
      title: "감정 발견형",
      desc: "감정을 새롭게 만나고 싶은 마음을 지녔습니다.",
      main: "『우당탕탕 잡았다, 내 감정!』",
      sub: "『순간포착! 이 감정, 대체 뭔데?!』"
    }
  };

  const r = results[resultType];

  document.getElementById("app").innerHTML = `
    <div class="result">
      <h2>당신은 <strong>${r.title}</strong></h2>
      <p>${r.desc}</p>
      <div class="book">
        <strong>📕 메인 추천</strong><br>${r.main}
      </div>
      <div class="book sub">
        <strong>📘 함께 읽으면 좋은 책</strong><br>${r.sub}
      </div>
      <p style="margin-top:20px;">이 결과를 친구에게 공유해보세요.</p>
    </div>
  `;
}

renderQuestion();
</script>

</body>
</html>
