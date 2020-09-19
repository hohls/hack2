<script>
 
export let id;

import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();

function sayHello() {
 
   if(0)
   {
   this.style.backgroundColor= '#94ce2d'
  	}
    dispatch('message', {
        text: id
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
		color: #94ce2d;
	}

	:global(body.dark-mode) button {
		background-color: #0084f6;
		color: white;
	}
</style>