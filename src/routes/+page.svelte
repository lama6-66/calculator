
<script lang="ts">
    
    import { onMount } from "svelte";


let equation: string="";

function Equation( value :string){
    equation+=value;
}

function space(){
    switch(equation.substring(equation.length-3, equation.length)){
        case " + ":
        case " * ":
        case " - ":
        case " / ":
        equation=equation.substring(0, equation.length-3);
        break;
        default:
        equation=equation.substring(0, equation.length-1);
    }



   /* equation=equation.substring(0, equation.length-1);
    if(equation.charAt(equation.length - 1)==' * '){
        equation=equation.substring(0, equation.length-1);
    }else{
        equation=equation.substring(0, equation.length-1);
    }

*/

}

function clear(){
    
    equation="";
}

function solve(){


    try{

   let answer  =eval(equation);
   if(answer == undefined) throw SyntaxError;
    }catch  (error){
        alert('error');
    }

}
 
function onkeyDown(e: KeyboardEvent) {
    let button =document.getElementById(e.key);
    button?.click();
    button?.focus();
   /* setTimeout(() =>{
        document.activeElement?.blur();
    }, 100);
    */
}




onMount(()=>{
let allButtons= document.getElementsByTagName('button');

for(let i=0;i<allButtons.length;i++){
    allButtons[i].addEventListener('click',() => {
        new Audio('/click.mp3').play();
    });
}
});


</script>

<svelte:window on:keydown|preventDefault={onkeyDown} />



<div  class="bg-white rounded-3xl grid grid-cols-4 gap-2 p-14 pt-15 font-normal shadow-2xl max-w-[20rem] ">
<div class="bg-slate-500 text-white rounded-x1 col-span-4 min-h-12 w-30 flex items-center px-5 mb-5 font-bold break-all">
{equation}
</div>

<button id="%" on:click={() => Equation(' / 100')} class="bg-blue-500 hover:bg-blue-600  "> 
    <svg xmlns="http://www.w3.org/2000/svg"
     width="1em" height="1em" viewBox="0 0 24 24">
     <path fill="none" stroke="currentColor" stroke-linecap="round" 
     stroke-linejoin="round"
      stroke-width="1.5" d="M17 19a2 2 0 1 1 0-4a2 2 0 0 1 0 4M7 9a2 2 0 1 1 0-4a2 2 0 0 1 0 4m12-4L5 19"/>
    </svg>


</button>
<button id="CE"  on:click={space} class="bg-yellow-400 flex items-center justify-center hover:bg-yellow-500 "> 
    <svg xmlns="http://www.w3.org/2000/svg"
      class="w-8 h-8"
    width="1em" height="1em" viewBox="0 0 24 24">
    <path fill="currentColor" d="M7.616 20q-.672 0-1.144-.472T6 18.385V6H5V5h4v-.77h6V5h4v1h-1v12.385q0 .69-.462 1.153T16.384 20zM17 6H7v12.385q0 
    .269.173.442t.443.173h8.769q.23 0 .423-.192t.192-.424zM9.808 17h1V8h-1zm3.384 0h1V8h-1zM7 6v13z"/>

</svg>

</button>
<button id="^" on:click={() => Equation('**')} class="bg-red-500 hover:bg-red-600 flex items-center justify-center "> 
    <svg xmlns="http://www.w3.org/2000/svg"
    class="w-6 h-6"
     width="1em" height="1em" viewBox="0 0 24 24">
     <path fill="currentColor" d="m15.38 3l2.39 5.75c-.22.93-.5 1.57-.77 
     1.95c-.33.48-.56.55-.81.55v1.5c.75 0 1.55-.4 2.05-1.19C19.87 8.94 22 3 22 3h-1.62l-1.69 4.05L17
      3zM3.42 8.59L2 10l4.79 4.79L2 19.59L3.41 21l4.8-4.79L13 21l1.41-1.41l-4.79-4.8L14.41 10L13 
      8.59l-4.79 4.79l-4.8-4.79z"/>
    </svg>


</button>
<button id="C" on:click={clear} class=" bg-orange-400 text-2xl hover:bg-orange-500"> C </button>
<button id="7" on:click={() => Equation('7')} class="hover:bg-slate-400"> 7 </button>
<button id="8" on:click={() => Equation('8')} class="hover:bg-slate-400" > 8 </button>
<button id="9" on:click={() => Equation('9')} class="hover:bg-slate-400"> 9 </button>
<button id="-" on:click={() => Equation(' - ')} class="bg-green-700 text-1xl hover:bg-green-800  "> 
    <svg xmlns="http://www.w3.org/2000/svg" 
    class="w-4"
    width="1em" height="1em" viewBox="0 0 512 512">
    <path fill="currentColor" d="M1 229.3h512v85.3H1z"/>
</svg>



</button>
<button id="4" on:click={() => Equation('4')} class="hover:bg-slate-400"> 4 </button>
<button id="5" on:click={() => Equation('5')} class="hover:bg-slate-400"> 5 </button>
<button id="6" on:click={() => Equation('6')} class="hover:bg-slate-400"> 6 </button>
<button id="/" on:click={() => Equation(' / ')} class="bg-sky-500 text-3xl hover:bg-sky-600"> 
    <svg xmlns="http://www.w3.org/2000/svg" 
    width="1em" height="1em" viewBox="0 0 24 24">
    <g fill="none" stroke="currentColor" stroke-linejoin="round">
        <path stroke-width="2.25" d="M12 6.5h.01v.01H12zm0 11h.01v.01H12z"/>
        <path stroke-linecap="round" stroke-width="1.5" d="M18 12H6"/></g></svg>


</button>
<button id="1" on:click={() => Equation('1')} class="hover:bg-slate-400"> 1 </button>
<button id="2" on:click={() => Equation('2')} class="hover:bg-slate-400"> 2 </button>
<button id="3" on:click={() => Equation('3')} class="hover:bg-slate-400"> 3 </button>
<button id="*" on:click={() => Equation(' * ')} class="bg-pink-600 text-3xl hover:bg-pink-700"> 
    <svg xmlns="http://www.w3.org/2000/svg" 
    width="1em" height="1em" viewBox="0 0 24 24">
    <path fill="none" stroke="currentColor" stroke-linecap="round" 
    stroke-linejoin="round" stroke-width="1.5" d="m18 6l-6 6m0 0l-6 6m6-6l6 6m-6-6L6 6" color="currentColor"/>
    </svg>




</button>
<button id="." on:click={( ) =>Equation(".") } class="hover:bg-slate-400"> . </button>
<button id="0" on:click={() => Equation('0')} class="hover:bg-slate-400"> 0 </button>
<button id="=" on:click={() => solve()} class="hover:bg-slate-400"> =  </button>
<button id="+" on:click={() => Equation(' + ')} class="bg-violet-500 text-2xl hover:bg-violet-600"> 
    <svg xmlns="http://www.w3.org/2000/svg" 
    width="1em" height="1em" viewBox="0 0 2048 2048">
    <path fill="currentColor" d="M1920 896v128h-896v896H896v-896H0V896h896V0h128v896z"/>
</svg>  


</button>
</div>
