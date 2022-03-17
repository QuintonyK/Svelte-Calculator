<script>

    let numbers = ["9","8","7","6","5","4","3","2","1","0",];
    let operators = ["Plus","Minus","Divide","Multiply","Equals","Clear",]

    var outputCurrent = "0";
    let outputPast = "0";
    let lastnr;
    let currentOperator;
    let sum;

    function handleClick(e){
        checkOutput(e)
    }

    function checkOutput(e){
        
        if (e == "Plus" || e == "Minus" || e == "Divide" || e == "Multiply" || e == "Equals" || e == "Clear"){
            handleOperator(e);
        }
        else{
            handleOutput(e);
        }
    }

    function handleOutput(e){
        if (outputCurrent == "0"){
            outputCurrent = "";
            outputCurrent = outputCurrent + e;
        }
        else{
            outputCurrent = outputCurrent + e;
        }
        
    }

    function handleOperator(e){
        switch (e){
            case "Plus":
                if (outputPast == "0"){
                    currentOperator = "+";
                    lastnr = outputCurrent;
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0";
                    break;
                }
                else{
                    lastnr = sum;
                    currentOperator = "+";
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0"
                    break;
                }
            case "Minus":
                if (outputPast == "0"){
                    currentOperator = "-";
                    lastnr = outputCurrent;
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0";
                    break;
                }
                else{
                    lastnr = sum;
                    currentOperator = "-";
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0"
                    break;
                }
            case "Divide":
                if (outputPast == "0"){
                    currentOperator = "/";
                    lastnr = outputCurrent;
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0";
                    break;
                }
                else{
                    lastnr = sum;
                    currentOperator = "/";
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0"
                    break;
                }
            case "Multiply":
                if (outputPast == "0"){
                    currentOperator = "*";
                    lastnr = outputCurrent;
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0";
                    break;
                }
                else{
                    lastnr = sum;
                    currentOperator = "*";
                    outputPast = lastnr + " " + currentOperator;
                    outputCurrent = "0"
                    break;
                }
            case "Equals":
                if(currentOperator == "+"){
                    Sum(currentOperator);
                    outputPast = outputPast + " " + outputCurrent;
                    outputCurrent = sum.toString(10);
                    break;
                }
                else if(currentOperator == "-"){
                    Sum(currentOperator);
                    outputPast = outputPast + " " + outputCurrent;
                    outputCurrent = sum.toString(10);
                    break;
                }
                else if(currentOperator == "/"){
                    Sum(currentOperator);
                    outputPast = outputPast + " " + outputCurrent;
                    outputCurrent = sum.toString(10);
                    break;
                }
                else if(currentOperator == "*"){
                    Sum(currentOperator);
                    outputPast = outputPast + " " + outputCurrent;
                    outputCurrent = sum.toString(10);
                    break;
                }
                else{
                    break;
                }
            case "Clear":
                outputCurrent = "0"
                outputPast = "0"
                break;
        }
    }

    function Sum (operator){
        switch (operator){
            case "+":
                sum = Number(lastnr) + Number(outputCurrent);
                break;
            case "-":
                sum = Number(lastnr) - Number(outputCurrent);
                break;
            case "/":
                sum = Number(lastnr) / Number(outputCurrent);
                break;
            case "*":
                sum = Number(lastnr) * Number(outputCurrent);
                break;
            default:
                break;
        }
    }

</script>

<div class="calculator">
    <div class="output"> <span class="past">{outputPast}</span> {outputCurrent}</div>
    <div class="input">
        {#each numbers as number}
            <button on:click={()=>{handleClick(number)}} id={"num"+number}>{number}</button>
        {/each}
        {#each operators as operator}
            <button on:click={()=>{handleClick(operator)}} id={"op"+operator}>
                {#if operator == "Plus"}
                    &#43;
                {:else if operator == "Minus"}
                    &#8722;
                {:else if operator == "Divide"}
                    &#247;
                {:else if operator == "Multiply"}
                    &#215;
                {:else if operator == "Equals"}
                    &#61;
                {:else if operator == "Clear"}
                    C
                {/if}
            </button>
        {/each}
    </div>
</div>

<style>
    .calculator{
        width: 500px;
        height: 500px;
        margin: .5rem;
        padding: .5rem;
        background-color: var(--primary);
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 60px 1fr;
        border: 2px solid var(--dark);
        border-radius: 1rem;
    }

    .output{
        margin: .5rem;
        margin-top: 1.5rem;
        padding: .5rem;
        padding-right: 1rem;
        padding-left: 1rem;
        background-color: #333333;
        text-align: right;
        align-self: center;
        border-radius: .5rem;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 20px 1fr;
        font-size: 1.4rem;
    }

    .output .past{
        color: #494949;
        font-size: 1rem;
        height: 20px;
    }

    .input{
        margin: 1.5rem;
        display: grid;
        justify-content: center;
        grid-template-columns: 100px 100px 100px 100px;
        grid-template-rows: 100px 100px 100px 100px;
    }

    button{
        margin: 2px;
        font-size: 2rem;
        border-radius: 1em;
        background-color: var(--primary);
        border: 2px solid var(--dark);
        transition: all .3s;
    }

    button:hover{
        background-color: var(--dark);
    }

    #num9{
        grid-area: 1/3;
    }

    #num5{
        grid-area: 2/2;
    }

    #num6{
        grid-area: 2/3 ;
    }

    #num1{
        grid-area: 3/1;
    }

    #num2{
        grid-area: 3/2;
    }

    #opPlus {
        grid-area: 1/4
    }

    #opMinus{
        grid-area: 2/4;
    }

    #opDivide{
        grid-area: 3/4;
    }

    #opEquals{
        grid-area: 4/3;
        background-color: rgb(0, 115, 192);
    }

    #opEquals:hover{
        background-color: rgb(0, 97, 161);
    }
    
    #opClear{
        grid-area: 4/1;
        background-color: rgb(255, 68, 0);
    }

    #opClear:hover{
        background-color: rgb(218, 59, 1);
    }

</style>