window.onload = function() {
  // Code for IDE
  var textareaCode = document.getElementById("textarea_code");
  var textareaLineNumbers = document.getElementById("textarea_line_numbers");
  ///////
  var ro = new ResizeObserver( entries => {
    for (let entry of entries) {
      const cr = entry.contentRect;
      textareaLineNumbers.style.height = cr.height + cr.top + cr.top;
    }
  });
  ro.observe(textareaCode);
  ///////
  textareaCode.addEventListener("keydown", function(event) {
    if (event.keyCode===9) {
      var v = this.value, s=this.selectionStart,e=this.selectionEnd;
      this.value = v.substring(0, s)+"\t"+v.substring(e);
      this.selectionStart=this.selectionEnd=s+1;
      event.preventDefault();
      return false;
    }
    if (event.keyCode===13) {
      var lineNumbers = document.getElementById("textarea_line_numbers");
      if (lineNumbers.value.length===2) {
        lineNumbers.value += "2\n";
        return false;
      }
      if (lineNumbers.value.length > 2) {
        var lineNumberString = lineNumbers.value;
        var lineNumberArray = lineNumberString.split("\n");
        var lastLineNumber = lineNumberArray[lineNumberArray.length - 2];
        var nextLineNumber = parseInt(lastLineNumber) + 1;
        lineNumbers.value += nextLineNumber + "\n";
      }
    }
    if (event.keyCode===8) {
      const textareaCodeValue = this.value;
      if (textareaCodeValue.length > 0) {
        var backspacedCharacter = textareaCodeValue.substring(this.selectionStart-1, this.selectionStart);
        const lineNumbers = document.getElementById("textarea_line_numbers");
        const lineNumberString = lineNumbers.value;
        if (backspacedCharacter === "\n") {
          var lineNumberArray = lineNumberString.split("\n");
          var slicedArray = lineNumberArray.slice(0,-2);
          var newString = slicedArray.join("\n");
          newString += "\n";
          lineNumbers.value = newString;
        }
      }
    }
  });
  textareaCode.addEventListener("scroll", function() {
    var y = textareaCode.scrollTop;
    document.getElementById("textarea_line_numbers").scrollTop = y;
  });
  // End code for IDE
};
