

<script>
let click_count = 0;
let id;

import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

function sayHello() {
     click_count =1;
   if(click_count==1)
   {
   this.style.backgroundColor= '#94ce2d'

   }
   else{
    this.style.backgroundColor= '#f76027'
   }

    dispatch('message', {
        text: 'id'
    });
};


</script>

<button on:click={sayHello}>
<slot/>
</button>

<style>
	button {
		background-color: #f76027;
		color: white;
		border: none;
		border-radius: 4px;
		padding: 0.5rem;
		text-transform: uppercase;
		
	}
    button:hover {
		background-position: 0;
		color: #aaa;
	}

	:global(body.dark-mode) button {
		background-color: #0084f6;
		color: white;
	}
</style>