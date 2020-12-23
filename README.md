# ko-customKeyboard
바닐라 javascript 한글 가상 키보드

###설명
키오스크 같이 input 눌렀을때 키보드가 지원되지 않을때 
사용할려고 만들었습니다.

[Hangul.js](https://github.com/e-/Hangul.js/)
를 사용했습니다. 짱멋집니다!


###코드예시

```html
<script src="./hangul.js" type="text/javascript"></script>
<script src="./keyboard.js" type="text/javascript"></script>
<body>
	<input id="myinput" type="" name="">
	<div id="keyboardzone"></div>
</body>
<script type="text/javascript">
	var keyboardzone = document.getElementById("keyboardzone");
	var input = document.getElementById("myinput");

	var keyboard = new customKeyboard(
		keyboardzone/*생성위치 태그*/,
		input/*input을 받을 태그*/, 
        function()/*클릭 했을때*/ {
            console.log("click : ", text);
        },
        function()/*esc 눌렀을때*/ {
            console.log("esc");
        },
        function(e)/*앤터 눌렀을때*/ {
            console.log("앤터 : ", text);
        }, 
        null/*키패드를 모양 값*/
        // {
        //     koNormal : [
        //         ['뒤로','1','2','3','4','5','6','7','8','9','0', 'backspace'],
        //         ['ㅂ', 'ㅈ', 'ㄷ', 'ㄱ', 'ㅅ', 'ㅛ', 'ㅕ', 'ㅑ', 'ㅐ', 'ㅔ'],
        //         ['ㅁ','ㄴ','ㅇ','ㄹ','ㅎ','ㅗ','ㅓ','ㅏ','ㅣ', 'enter'],
        //         ['shift','ㅋ','ㅌ','ㅊ','ㅍ','ㅠ','ㅜ','ㅡ','한/영'],
        //         ["space"]
        //     ], 
        //     koShift : [
        //         ['뒤로','!','@','#','$','%','^','&','*','(',')', 'backspace'],
        //         ['ㅃ', 'ㅉ', 'ㄸ', 'ㄲ', 'ㅆ', 'ㅛ', 'ㅕ', 'ㅑ', 'ㅒ', 'ㅖ'],
        //         ['ㅁ','ㄴ','ㅇ','ㄹ','ㅎ','ㅗ','ㅓ','ㅏ','ㅣ', 'enter'],
        //         ['shift','ㅋ','ㅌ','ㅊ','ㅍ','ㅠ','ㅜ','ㅡ','한/영'],
        //         ["space"]
        //     ],
        //     enNormal : [
        //         ['뒤로','1','2','3','4','5','6','7','8','9','0', 'backspace'],
        //         ['q','w','e','r','t','y','u','i','o','p'],
        //         ['a','s','d','f','g','h','j','k','l','enter'],
        //         ['shift','z','x','c','v','b','n','m','한/영'],
        //         ["space"]
        //     ],
        //     enShift : [
        //         ['뒤로','!','@','#','$','%','^','&','*','(',')', 'backspace'],
        //         ['Q','W','E','R','T','Y','U','I','O','P'],
        //         ['A','S','D','F','G','H','J','K','L','enter'],
        //         ['shift','Z','X','C','V','B','N','M','한/영'],
        //         ["space"]
        //     ]
        // }
    );

	input.addEventListener("click", function() {
        //input 태그를 자신으로 설정
        keyboard.setInput(this);
        //키패드 클릭 이벤트 설정
        keyboard.setClick(function(text) {
            console.log("input을 click한 후 : ", text);
        })
        //앤터 이벤트 설정
        keyboard.setEnter(function(e) {
            menu3searching(e)
        });
    })
</script>
```
