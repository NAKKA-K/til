# Stop event
javascriptを使用して、そのアイテムが持つ機能を停止する方法

    let textBox = document.getElementById('my_textbox')
    
    function checkName(event){
      const charCode = event.charCode;

      if(charCode == 20){
        event.preventDefault(); //機能停止コード
        alert("その文字は入力してはいけません");
      }
    }

    textBox.addEventListener('keypress', checkName, false);

上記の例は、charcodeが20の文字を入力されたときのコード。
その時、textboxの機能を停止して、その文字を入力させず、アラートを出すようにしている。

