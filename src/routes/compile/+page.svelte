<script>    
    import { slide } from "svelte/transition";
    let flag=false;
    const toggle=()=>{flag=!flag;}
    import {getCode} from './getCode';
    let program_lang='Python';
    let program_code=getCode[program_lang]["code"];
    let program_input='';
    let display='';

    //function to update selection in 'Selected Language'
    function updateCode(){
        program_code= getCode[program_lang]["code"];
    }

    async function getApi(){
        //  API URL 
        const url = 'https://code-compiler.p.rapidapi.com/v2';
        const options = {
            method: 'POST',
            headers: {
                'content-type': 'application/x-www-form-urlencoded',
                'X-RapidAPI-Key':  import.meta.env.VITE_API_KEY,
                'X-RapidAPI-Host': 'code-compiler.p.rapidapi.com'
            },
            body: new URLSearchParams({
                LanguageChoice: getCode[program_lang]["value"],
                Program:program_code,
                Input:program_input
            })
        };

        //  Fetch URL  
        const response=await fetch(url,options);
        const result=await response.json();

        // Ternary operator to save response in 'display' variable
        display = (response.status!==504)       ?
        (
            (result.Result!=null)  ?  result.Result  :  "Error\n"+result.Errors
        )       :      "API Timeout. Please try again!!";

        //  Scroll to bottom to display result  
        window.scrollTo({ top: document.body.scrollHeight, behavior: "smooth" });
    }
    
    //  Function to enter 'indent' when Tab is entered instead of focusing next input field 
    function getConsole(event){
        if (event.key === "Tab") {
            event.preventDefault();
            document.execCommand("insertText", false, "\t");
        }
    }

    //  Function to copy output 
    function copy_output(){
        navigator.clipboard.writeText(display);
        alert("Output Copied!!");    
    }
</script>

<div class="code text-column">
    <p>Code Compiler</p>
    <div class="menu">
        <div class="menu-lang">
        Selected Language : {program_lang}
        </div>
        <button class="more" on:click={toggle}>More</button>
    </div>

    {#if flag}
    <div class="radioOptions" on:change={updateCode} transition:slide={{ duration: 700 }}>
        {#each Object.keys(getCode) as item}
            <input class="radio-label" bind:group={program_lang} type="radio" name="language" value={item} id={item}>
            <label class="button-label" for={item}>{item}</label>
        {/each}        
    </div>
    {/if}     

    <div class="input">
        <div style="padding-right:50px ;">
            <span>Code :</span><br>
            <textarea bind:value={program_code} on:keydown={getConsole} class="code-inp" name="code-inp" id="code-inp"></textarea>
        </div>
        <div>
            <span>Input:</span><br>
            <textarea bind:value={program_input} type="text"  class="inp" name="inp" id="inp" style=""></textarea><br>
            <button on:click={getApi} type="button" class="compile" id="compile">Run </button>
        </div>        
    </div>

      
    <div class="output">
        <div class="ot-menu">
            <span>Output :</span>
            <button on:click={copy_output}>Copy</button>
        </div>
        <pre class="opt">{display}</pre>
    </div>
</div>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Noto+Sans:wght@600&display=swap');
    button{
        appearance: button;
		backface-visibility: hidden;
		background-color: initial;
		box-shadow: 4px 4px 1px 0px rgba(0,0,0,0.75);
		color: rgb(0, 0, 0);
		cursor: pointer;
		display: inline-block;
		font-family: Inter,-apple-system,system-ui,Roboto,"Helvetica Neue",Arial,sans-serif;
		font-size:20px;
		font-weight:bold;
		height: 40px;
		outline: 0;
		overflow: hidden;
		padding: 0 20px;
		pointer-events: auto;
		position: relative;
		text-align: center;
		text-transform: none;
		user-select: none;
		-webkit-user-select: none;
		vertical-align: top;
		white-space: nowrap;
		z-index: 9;
		border: 0;
		transition: all .2s,box-shadow .08s ease-in;
		text-decoration: none;
    }
    button:hover{
        transform: scale(1.1);
    }

    /*  Code Container  */
    .code{
        min-width: 62rem;
        padding-left: 6rem;
        font-size: 20px;
        border-radius: 25px;
        color:#F1FD4A;
        box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		-webkit-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
		-moz-box-shadow: 10px 10px 5px 0px rgba(0,0,0,0.75);
        background: hsla(356, 76%, 50%, 1);
        background: linear-gradient(90deg, hsla(356, 76%, 50%, 1) 0%, hsla(14, 63%, 36%, 1) 100%);
        background: -moz-linear-gradient(90deg, hsla(356, 76%, 50%, 1) 0%, hsla(14, 63%, 36%, 1) 100%);
        background: -webkit-linear-gradient(90deg, hsla(356, 76%, 50%, 1) 0%, hsla(14, 63%, 36%, 1) 100%);
    }
    .code p{
        font-size: 35px;
        width: 20rem;
        position: relative;
        left:34%;
    }
    
    /*  Menu Bar    */
    .radioOptions{
        max-width:55rem;
    }
    .radio-label{
        display: none;
    }
    .menu{
        width: 55rem;
        display: flex;
        justify-content:space-between;
    }
    .button-label {
        display: inline-block;
        padding: 10px 20px 10px;
        margin: 0.3em 0.1em;
        cursor: pointer;
        color:#ffffff ;
        border-radius: 0.25em;
        background: rgb(15, 61, 189);
        transition: 0.2s;
        user-select: none;
    }
    .radio-label:checked + .button-label {
        background: rgb(10, 255, 112);
        color: rgb(0, 0, 0);  
        font-weight: bold;
    }
    .button-label:hover {
        transform: scale(1.1);
    }
    .menu .more{
        background-color: rgb(11, 191, 236);
        color: #000;
        width:7rem;
        margin-bottom: 10px;
        border-radius: 10px;
        height: 2rem;
    }

    /*  Code Input  */
    .input{
        display: flex;
        flex-direction:row;
        padding-top: 20px;
    }
    .code-inp{
        width:500px;
        height: 200px;
        resize: none;
        font-family: 'Noto Sans', sans-serif;
        font-size: 20px;
    }
    .inp{
        height:120px;
        width:20rem;
        font-family: 'Noto Sans', sans-serif;
        font-size: 18px;
    }
    .compile{
        color:rgb(0, 0, 0);
        margin-top:1rem;
        margin-left:6rem;
        width:10rem;
        background: #ad5389;
        background: linear-gradient(0deg, rgba(20,167,62,1) 0%, rgba(102,247,113,1) 100%);
        border-radius: 15px;
    }
    
    /*  Code Output */
    .output{
        width: 55rem;
        margin-top: 20px;
        padding-bottom: 2rem;
    }
    .ot-menu{
        display: flex;
        justify-content: space-between;
    }
    .ot-menu button{
        display: inline-block;
        outline: none;
        cursor: pointer;
        padding: 0 16px;
        background-color: #0070d2;
        border-radius: 0.25rem;
        border: 1px solid #0070d2;
        color: #fff;
        text-align: center;
        height:35px;
    }
    .ot-menu button:hover{
        background-color: #005fb2;  
        border-color: #005fb2;
    }
    .opt{
        font-size: 20px;
    }
</style>
