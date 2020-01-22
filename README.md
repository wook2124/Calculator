# 001- 계산기 만들기
</html>
  <head>
    <link rel="stylesheet" href="style.css">
    <script defer type="text/javascript"
      src="script.js"></script>
  </head>
  <body>
    <div id="calculator">
      <span>깃똥찬 계산기</span><br>
      <input id="formula-input"
        type="text"
        placeholder="수식을 입력하세요."/>
      <div id="calc-history"></div>
    </div>
  </body>
</html>


#calculator {
  background-color: #24ffbd;
  border-radius: 12px;
  width: 240px;
  margin: 240px;
  padding: 24px;
  text-align: center;
}

#calculator span {
  font-size: 1.5em;
  font-weight: bold;
  color: white;
  text-shadow: 0px 0px 2px rgba(0, 0, 0, 33);
}

#calculator #formula-input {
  width: 242;
  margin-top: 8px;
  height: 36px;
  line-height: 36px;
  font-size: 1.1em;
  letter-spacing: 3px;
  border: 0;
  text-align: center;
}


var formulaInput = document.getElementById("formula-input");
var calcHistDiv = document.getElementById("calc-history");

formulaInput.addEventListener("keyup", function(e) {
 if (e.code === "Enter")
  calculate();   
})

function calculate() {

 // 입력칸의 문자열이 사칙연산 형식이 맞는지 확인
 var fm = formulaInput.value;
 var formulaRegex = /^\d+(.\d+)?[+\-*/]{1}\d+(.\d+)?$/;
 var fromulaValid = formulaRegex.test(fm);

 var resultText = "노";
 if (formulaValid) {
   // 형식에 맞을 시 식을 계산하고 결과 문자열을 사용
   var answer;
   eval('answer=' + fm);
   resultText = fm + " = ";
   resultText
   += (answer % 1 > 0 ? answer.toFixed(2) : answer.toString());   
 }

 // calc-history 상자에 넣을 또 다른 상자를 생성하고 내용을 설정한 뒤 삽입
 var resultDiv = document.createElement("DIV");
 resultDiv.appendChild(document.createTextNode(resultText));
 if (!formulaValid)
   resultDiv.classList.add("invalid");
 calcHistDiv.insertBefore(resultDiv, calcHistDiv.firstChild); 
 
 // 입력칸은 빈칸으로    
 formulaInput.value = "";
}


▶HTML = Hyper Text Markup Language
 화면들에 이것들을 놓여있어라! 하고 갖다놓는 수단

▶CSS = Cascading Style Sheets
 HTML을 올려놓은 이것들을 이렇게 보여라! 하고 꾸며주는 [문서]

▶JavaScript = 브라우저에서 다양한 일을 수행하고 HTML로 올려놓은 요소들을 변형시키거나 직접 만들어내기까지 함
