# AdamsCalculator
<html>
  <head>
   <style>#calculator {
    display: flex;
    flex-direction: column;
    width: 16rem;
    margin:auto;
    background-color: black;
    border: solid 5px #000;
  }
  
  #screen {
    background-color: white;
    height: 4rem;
    width: 90%;
    margin: 10px auto;
    font-size: 2rem;
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }
  
  #numbers {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  
  .button {
      background-color: red;
      width: 3rem;
      height: 3rem;
      margin: .5rem;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 2rem;
      font-weight: bold;
      box-shadow: 3px 3px blue;
  }
  

  .button:active {
    box-shadow: 0px 0px;
  }
  
  .operator {
    background-color: red;
      margin-bottom: .25rem;
      height:2rem;
      width:3rem;
    }
  
  #buttons {
    display: flex;
    justify-content: space-around;
    cursor: pointer;
  }
  
  #operators {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  
  }
  
  #clear,
  #equal {
    background-color: red;
  }</style>
  </html>
    </div>
    <div id="calculator">
      <div id="screen"></div>
      <div id="buttons">
      <div id="numbers">
        <div class="number button">1</div>
        <div class="number button">2</div>
        <div class="number button">3</div>
        <div class="number button">4</div>
        <div class="number button">5</div>
        <div class="number button">6</div>
        <div class="number button">7</div>
        <div class="number button">8</div>
        <div class="number button">9</div>
        <div class="number button">0</div>
        <div class="number button">.</div>
        <div class="button" id="equal">=</div>
      </div>
      <div id="operators">
        <div class="operator button" id="plus">+</div>
        <div class="operator button" id="minus">-</div>
        <div class="operator button" id="multiply">x</div>
        <div class="operator button" id="divide">/</div>
        <div class="button" id="clear">C</div>
    </div>
  </div> 
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

  <script>var currentNumber = 1;
    var num1 = null;
    var num2 = null;
    var click = 0;
    
    var $screen = $("#screen");
    var $number = $(".number");
    
    
    $number.on('click', function() {
          click++;
        if (click > 12){
          return;
        }
        var numberPressed = $(this).html();
        $screen.append(numberPressed);
        $("#clear").css('background-color', '#cc1423');
    
      if (currentNumber == 1) {
        if (num1 == null) {
          num1 = numberPressed;
        } else {
          num1 = num1 + numberPressed;
        }
      }
      if (currentNumber == 2) {
        if (num2 == null) {
          num2 = numberPressed;
        } else {
          num2 = num2 + numberPressed;
        }
        $("#equal").css('background-color', '#cc1423');
      }
    });
    
      function more(){
        if (click > 12){
        }
        if (currentNumber == 2) {
          findAnswer();
          $screen.empty();
          $screen.append(num1);
        }
        currentNumber = 2;
      }
    
            $("#plus").on('click', function()
              {
                if(num1 != null) {
                  more();
                 $screen.append("+");
                 op = "+";
               };
               return;
               })
    
                $("#minus").on('click', function()
                  {
                    if(num1 != null) {
                      more();
                     $screen.append("-");
                     op = "-";
                   };
                   return;
                  })
    
                    $("#multiply").on('click', function()
                        {
                          if(num1 != null) {
                            more();
                         $screen.append("x");
                         op = "x";
                       };
                       return;
                       })
    
                        $("#divide").on('click', function()
                            {
                              if(num1 != null) {
                              more();
                             $screen.append("/");
                             op = "/";
                           };
                           return;
                           })
    
          $("#clear").on('click', function()
            {
              $screen.empty();
              num1 = null;
              num2 = null;
              currentNumber = 1;
              click = 0;
              $("#clear").css('background-color', 'gray');
              $("#equal").css('background-color', 'gray');
            });
    
            function findAnswer() {
              num1 = parseFloat(num1);
              num2 = parseFloat(num2);
                if (op == "+") {
                  answer = num1 + num2;
                }
                if (op == "-") {
                  answer = num1 - num2;
                }
                if (op == "x") {
                  answer = num1 * num2;
                }
                if (op == "/") {
                  answer = num1 / num2;
                }
                num1 = answer;
                num2 = null;
                currentNumber = 1;
            }
    
                            $("#equal").on('click', function()
                                {
                                  var element = document.getElementById('equal');
                                  var style = window.getComputedStyle(element);
                                  var backgroundColor = "background-color";
                                  var buttonColor = element.style.backgroundColor;
                                  if(buttonColor == 'gray') {
                                    return;
                                  }
                                $screen.append("=");
                                 findAnswer();
                                 console.log(answer);
                                 a = answer;
                                 answer = a.toFixed(1);
                                 console.log(answer);
                                 if (click > 8){
                                   $screen.empty();
                                   var answerLength = answer.toString();
                                   click = answerLength.length;
                                 }
                                   $screen.append(answer);
                                   $("#equal").css('background-color', 'gray');
                                })</script>
</body>
</html>
