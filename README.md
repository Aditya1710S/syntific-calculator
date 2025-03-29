html.
<!-- goal: use no images -->

<!-- it might not turn up correctly on your system because you wouldn't have the fancy fonts i used and codepen free doesn't allow me to upload assets :( -->

<!-- here's how it's supposed to look: https://imgur.com/a/IQKSUCW -->

<!-- compare it to an image of the actual calculator: https://imgur.com/M3z8UCm -->

<!-- 
fonts used:
    - 'Helvetica' for buttons etc
    - 'Eurostile Extended Black' for Casio logo
    - 'Computer Modern' for "fx-82MS" in the top-right corner
    - 'Pirulen' for "SVPAM"
    - 'Scientifc Calculator LED' for "571^2"
    - 'Segment7Standard' for "326041."
-->
<!DOCTYPE html>
<html>

<head>
    <title>Scientific Calculator using HTML, CSS and Js</title>
    <link rel="stylesheet" href="casio.css">
    <script src="casio.js"></script>

<div class="calculator">
    <span class="logo">Casio</span>
    <span class="model">fx-82MS</span>
    <span class="svpam">S-V.P.A.M.</span>
    
    <div class="screen">
        <div class="input">571^2</div>
        <div class="main-display">326041.</div>
    </div>
    
    <div class="modifiers">
        <button class="shift center-shift" tabindex="1"></button>
        <button class="alpha center-alpha" tabindex="2"></button>
        <button class="on center-shift" tabindex="4"></button>
        <button class="mode" tabindex="3"></button>
    </div>
    
    <div class="replay">Replay</div>
    <!-- 
    <button class="nav up">▲</button>
    <button class="nav down">▼</button>
    <button class="nav left">◀︎</button>
    <button class="nav right">▶︎</button> 
    -->

    <table class="function-keys">
        <tr>
            <td><button class="reciprocal center-shift">x<span class="sup">-1</span></button></td>
            <td><button class="combin center-shift">nCr</button></td>
            <td></td>
            <td></td>
            <td><button class="pol">Pol(</button></td>
            <td><button class="cube center-shift">x<span class="sup">3</span></button></td>
        </tr>
        <tr>
            <td><button class="frac center-shift">a<span class="sup">b</span>/<span class="xxs">c</span></button></td>
            <td><button>&radic;</button></td>
            <td><button class="square">x<span class="sup">2</span></button></td>
            <td><button class="pow center-shift">^</button></td>
            <td><button class="log center-shift">log</button></td>
            <td><button class="ln">ln</button></td>
        </tr>
        <tr>
            <td><button class="minus">(&minus;)</button></td>
            <td><button class="deg">&deg;&prime;&Prime;</button></td>
            <td><button class="hyp">hyp</button></td>
            <td><button class="sin">sin</button></td>
            <td><button class="cos">cos</button></td>
            <td><button class="tan">tan</button></td>
        </tr>
        <tr>
            <td><button class="rcl center-shift">RCL</button></td>
            <td><button class="eng center-shift">ENG</button></td>
            <td><button class="open-paren">(</button></td>
            <td><button class="close-paren">)</button></td>
            <td><button class="comma">,</button></td>
            <td><button class="mem-plus">M+</button></td>
        </tr>
    </table>
    
    <table class="basic-keys">
        <tr>
            <td><button>7</button></td>
            <td><button>8</button></td>
            <td><button>9</button></td>
            <td><button class="pink del center-shift">DEL</button></td>
            <td><button class="pink ac center-shift">AC</button></td>
        </tr>
        <tr>
            <td><button>4</button></td>
            <td><button>5</button></td>
            <td><button>6</button></td>
            <td><button>×</button></td>
            <td><button>&divide;</button></td>
        </tr>
        <tr>
            <td><button class="one center-shift">1</button></td>
            <td><button class="two center-shift">2</button></td>
            <td><button>3</button></td>
            <td><button>+</button></td>
            <td><button>−</button></td>
        </tr>
        <tr>
            <td><button class="zero center-shift">0</button></td>
            <td><button class="period center-shift">.</button></td>
            <td><button class="exp center-shift">EXP</button></td>
            <td><button class="ans center-shift">Ans</button></td>
            <td><button class="equals center-shift">=</button></td>
        </tr>
    </table>
</div>

css.
body {
    background: linear-gradient(135deg, #FAD7A1 10%, #E96D71 100%);
}

.calculator {
    width: 18rem;
    height: 35rem;
    background: hsl(208, 28%, 35%);
    background: linear-gradient(to top, hsl(208, 30%, 35%), hsl(208, 30%, 40%));
    margin: 0 auto;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    border-bottom-left-radius: 100px 30px;
    border-bottom-right-radius: 100px 30px;
    position: absolute;
    top: 50%;
    transform: translateY(-50%) translatex(-50%);
    left: 50%;
    padding: 1.5rem;
    color: hsl(225, 20%, 84%);
    font-family: Helvetica;
    box-shadow: 0 0 50px 5px hsla(0, 0%, 0%, .5);
}

.logo, .model, .svpam {
    font-size: 90%;
}

.logo {
    font-family: 'Eurostile Extended', Impact;
    text-transform: uppercase;
}

.model {
    float: right;
    font-style: italic;
    font-family: CMU;
}

.svpam {
    width: 100%;
    text-align: center;
    display: inline-block;
    color: hsl(353, 50%, 70%);
    margin-top: .75em;
    font-family: pirulen;
}

.screen {
    width: 100%;
    height: 4rem;
    background: hsl(190, 20%, 88%);
    border-radius: 4px;
    box-shadow: inset 0 0 5px black;
    margin: 1em 0;
    color: black;
}

.screen .input {
    font-family: 'Scientific Calculator LCD', monospace;
    font-size: 1rem;
    position: relative;
    top: 12px;
    left: 12px;
}

.screen .main-display {
    font-family: 'Segment7Standard', monospace;
    font-size: 2rem;
    text-align: right;
    vertical-align: bottom;
    width: 275.2px;
    display: block;
    position: absolute;
    padding: .4rem;
    overflow-x: hidden;
}

button {
    text-align: center;
    cursor: pointer;
    padding: 5px;
    border: 0 white none;
    box-sizing: border-box;
    color: hsl(225, 20%, 84%);
    position: relative;
    box-shadow: 2px 2px 5px 0 hsla(0, 0%, 0%, .75);
}

table {
    width: 100%;
    border-collapse: collapse;
}

td {
    text-align: center;
}

.modifiers {
    margin: 1.5rem 0 1.75rem 0;
}

.modifiers button {
    width: 2.35rem;
    height: 1.25rem;
    border-radius: 15px;
    position: relative;
    margin-right: .75rem;
    background: hsl(221, 14%, 66%);
    background: linear-gradient(to top, hsl(221, 14%, 66%), hsl(221, 14%, 71%));
}

.modifiers button::before, .modifiers button::after {
    text-transform: uppercase;
}

.mode::before, .on::before {
    color: hsl(225, 20%, 84%);
}

.shift {
    left: 0;
}

.alpha {
    top: 5px;
}

.mode {
    float: right;
    top: 11px;
}

.on {
    float: right;
    right: 0;
    margin-right: .5em!important;
}

.shift::before {content: "Shift";}
.alpha::after {content: "Alpha";}
.mode::before {content: "Mode"; left: -9px}
.mode::after {content: "CLR"; right: -9px; color: hsl(34, 68%, 72%);}
.on::before {content: "ON";}

.replay {
    background: linear-gradient(to top, hsl(221, 14%, 66%), hsl(221, 14%, 71%));
    width: 78px;
    height: 70px;
    line-height: 70px;
    position: absolute;
    left: 38%;
    top: 30%;
    border-radius: 125px;
    text-transform: uppercase;
    font-size: 9px;
    text-align: center;
    vertical-align: middle;
    box-shadow: 2px 2px 5px 0 hsla(0, 0%, 0%, .75);
}

button.nav {
    position: absolute;
    background: none;
    box-shadow: none;
}

.function-keys {
    margin: 1.5rem 0 .75rem 0;
}

.function-keys button {
    background: hsl(198, 39%, 23%);
    background: linear-gradient(to top, hsl(198, 39%, 23%), hsl(198, 39%, 28%));
    font-size: small;
    width: 2.25rem;
    height: 1.5rem;
    border-radius: 5px;
}

.function-keys td {
    padding-bottom: 1rem;
    padding-right: .25rem;
}

.basic-keys {}
.basic-keys button {
    width: 2.5rem;
    height: 1.75rem;
    background: hsl(221, 14%, 66%);
    background: linear-gradient(to top, hsl(221, 14%, 66%), hsl(221, 14%, 71%));
    border-radius: 3px 3px 7px 7px;
}

.basic-keys td {
    padding-bottom: 1rem;
    padding-right: .25rem;
}

.basic-keys tr:last-child td {
    padding-bottom: 0;
}

button.pink {
    background: hsl(353, 50%, 70%);
    background: linear-gradient(to top, hsl(353, 50%, 70%), hsl(353, 50%, 75%));
}

button::before, button::after {
    position: absolute;
    font-size: 9px;
    top: -13px;
    display: block;
    width: 100%;
    display: inline-block;
}

/* shift */
button::before {
    color: hsl(34, 68%, 72%);
    left: 0;
    text-align: left;
}

/* alpha */
button::after {
    color: hsl(353, 50%, 70%);
    right: 0;
    text-align: right;
}

.center-shift::before, .center-alpha::after {
    text-align: center;
}

.del::before {content: "INS";}
.ac::before {content: "OFF";}
.reciprocal::before {content: "x!";}
.combin::before {content: "nPr";}
.pol::before {content: "Rec(";}
.pol::after {content: ":";}
.cube::before {content: "\221b";}
.frac::before {content: "d/c";}
.pow::before {content: "ˣ \221A"}
.log::before {content: "10 ˣ";}
.ln::before {content: "e ˣ";}
.ln::after {content: "e";}
.minus::before {content: "";}
.minus::after {content: "A";}
.deg::before {content: "\2190";}
.deg::after {content: "B";}
.hyp::after {content: "C";}
.sin::before {content: "sin \207b\b9";}
.cos::before {content: "cos \207b\b9";}
.tan::before {content: "tan \207b\b9";}
.sin::after {content: "D";}
.cos::after {content: "E";}
.tan::after {content: "F";}
.rcl::before {content: "STO";}
.eng::before {content: "\2190";}
.close::paren:after {content: "X";}
.comma::before {content: ";";}
.comma::after {content: "Y";}
.mem-plus::before {content: "M-";}
.mem-plus::after {content: "M";}
.zero::before {content: "Rnd";}
.period::before {content: "Ran#";}
.exp::before {content: "\03c0";}
.ans::before {content: "DRG\25ba";}
.equals::before {content: "%";}
.one::before {content: "S-SUM"; font-size: 8px; top: -10px}
.two::before {content: "S-VAR"; font-size: 8px; top: -10px}

/* jazzy 'x' */
/* .reciprocal, .square {} */

button span.sup {
    font-size: xx-small!important; 
    vertical-align: super;
}

.sub {
    font-size: xx-small; 
    vertical-align: bottom;
}

.xxs {
    font-size: xx-small;
}

java script.

document.addEventListener("DOMContentLoaded", function () {
    const inputDisplay = document.querySelector(".input");
    const mainDisplay = document.querySelector(".main-display");
    let currentInput = "";
    let previousAnswer = "";

    // Function to convert degrees to radians
    function degToRad(degrees) {
        return degrees * (Math.PI / 180);
    }

    // Function to convert radians to degrees
    function radToDeg(radians) {
        return radians * (180 / Math.PI);
    }

    document.querySelectorAll("button").forEach(button => {
        button.addEventListener("click", function () {
            const value = this.textContent.trim();

            if (value === "AC") {
                currentInput = "";
                mainDisplay.textContent = "0";
                inputDisplay.textContent = "";
            } else if (value === "DEL") {
                currentInput = currentInput.slice(0, -1);
            } else if (value === "=") {
                try {
                    let expression = currentInput
                        .replace(/×/g, "*")
                        .replace(/÷/g, "/");

                    // Handle trigonometric calculations
                    expression = expression.replace(/sin\(([^)]+)\)/g, (_, x) => `Math.sin(degToRad(${x}))`);
                    expression = expression.replace(/cos\(([^)]+)\)/g, (_, x) => `Math.cos(degToRad(${x}))`);
                    expression = expression.replace(/tan\(([^)]+)\)/g, (_, x) => `Math.tan(degToRad(${x}))`);

                    // Handle inverse trigonometric functions
                    expression = expression.replace(/sin⁻¹\(([^)]+)\)/g, (_, x) => `radToDeg(Math.asin(${x}))`);
                    expression = expression.replace(/cos⁻¹\(([^)]+)\)/g, (_, x) => `radToDeg(Math.acos(${x}))`);
                    expression = expression.replace(/tan⁻¹\(([^)]+)\)/g, (_, x) => `radToDeg(Math.atan(${x}))`);

                    let result = eval(expression);
                    previousAnswer = result;
                    mainDisplay.textContent = result;
                    currentInput = "";
                } catch (error) {
                    mainDisplay.textContent = "Error";
                }
            } else if (value === "Ans") {
                currentInput += previousAnswer;
            } else {
                currentInput += value;
            }

            inputDisplay.textContent = currentInput;
        });
    });
});


let calculator_buttons = [
    {
        name : "rad",
        symbol : "Rad",
        formula : false,
        type : "key"
    },
    {
        name : "deg",
        symbol : "Deg",
        formula : false,
        type : "key"
    },
    {
        name : "square-root",
        symbol : "√",
        formula : "Math.sqrt",
        type : "math_function"
    },
    {
        name : "square",
        symbol : "x²",
        formula : POWER,
        type : "math_function"
    },
    {
        name : "open-parenthesis",
        symbol : "(",
        formula : "(",
        type : "number"
    },
    {
        name : "close-parenthesis",
        symbol : ")",
        formula : ")",
        type : "number"
    },
    {
        name : "clear",
        symbol : "C",
        formula : false,
        type : "key"
    },
    {
        name : "delete",
        symbol : "⌫",
        formula : false,
        type : "key"
    },
    {
        name : "pi",
        symbol : "π",
        formula : "Math.PI",
        type : "number"
    },
    {
        name : "cos",
        symbol : "cos",
        formula : "trigo(Math.cos,",
        type : "trigo_function"
    },{
        name : "sin",
        symbol : "sin",
        formula : "trigo(Math.sin,",
        type : "trigo_function"
    },{
        name : "tan",
        symbol : "tan",
        formula : "trigo(Math.tan,",
        type : "trigo_function"
    },{
        name : "7",
        symbol : 7,
        formula : 7,
        type : "number"
    },{
        name : "8",
        symbol : 8,
        formula : 8,
        type : "number"
    },{
        name : "9",
        symbol : 9,
        formula : 9,
        type : "number"
    },
    {
        name : "division",
        symbol : "÷",
        formula : "/",
        type : "operator"
    },
    {
        name : "e",
        symbol : "e",
        formula : "Math.E",
        type : "number"
    },
    {
        name : "acos",
        symbol : "acos",
        formula : "inv_trigo(Math.acos,",
        type : "trigo_function"
    },{
        name : "asin",
        symbol : "asin",
        formula : "inv_trigo(Math.asin,",
        type : "trigo_function"
    },{
        name : "atan",
        symbol : "atan",
        formula : "inv_trigo(Math.atan,",
        type : "trigo_function"
    },
    {
        name : "4",
        symbol : 4,
        formula : 4,
        type : "number"
    },{
        name : "5",
        symbol : 5,
        formula : 5,
        type : "number"
    },{
        name : "6",
        symbol : 6,
        formula : 6,
        type : "number"
    },{
        name : "multiplication",
        symbol : "×",
        formula : "*",
        type : "operator"
    },{
        name : "factorial",
        symbol : "×!",
        formula : FACTORIAL,
        type : "math_function"
    },{
        name : "exp",
        symbol : "exp",
        formula : "Math.exp",
        type : "math_function"
    },{
        name : "ln",
        symbol : "ln",
        formula : "Math.log",
        type : "math_function"
    },{
        name : "log",
        symbol : "log",
        formula : "Math.log10",
        type : "math_function"
    },{
        name : "1",
        symbol : 1,
        formula : 1,
        type : "number"
    },{
        name : "2",
        symbol : 2,
        formula : 2,
        type : "number"
    },{
        name : "3",
        symbol : 3,
        formula : 3,
        type : "number"
    },{
        name : "subtraction",
        symbol : "–",
        formula : "-",
        type : "operator"
    },{
        name : "power",
        symbol : "x<span>y</span>",
        formula : POWER,
        type : "math_function"
    },{
        name : "ANS",
        symbol : "ANS",
        formula : "ans",
        type : "number"
    },{
        name : "percent",
        symbol : "%",
        formula : "/100",
        type : "number"
    },{
        name : "comma",
        symbol : ".",
        formula : ".",
        type : "number"
    },{
        name : "0",
        symbol : 0,
        formula : 0,
        type : "number"
    },{
        name : "calculate",
        symbol : "=",
        formula : "=",
        type : "calculate"
    },{
        name : "addition",
        symbol : "+",
        formula : "+",
        type : "operator"
    }
];

// GAMMA FUNCTINON
function gamma(n) {  // accurate to about 15 decimal places
    //some magic constants 
    var g = 7, // g represents the precision desired, p is the values of p[i] to plug into Lanczos' formula
        p = [0.99999999999980993, 676.5203681218851, -1259.1392167224028, 771.32342877765313, -176.61502916214059, 12.507343278686905, -0.13857109526572012, 9.9843695780195716e-6, 1.5056327351493116e-7];
    if(n < 0.5) {
      return Math.PI / Math.sin(n * Math.PI) / gamma(1 - n);
    }
    else {
      n--;
      var x = p[0];
      for(var i = 1; i < g + 2; i++) {
        x += p[i] / (n + i);
      }
      var t = n + g + 0.5;
      return Math.sqrt(2 * Math.PI) * Math.pow(t, (n + 0.5)) * Math.exp(-t) * x;
    }
}

 
