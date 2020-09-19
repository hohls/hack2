
 <script>
	import Button from './Button.svelte'
	let question = 'hole von json';
  let a1 = "OK"
  export let numberWins;
  import API from '../store/config';

   export let closeHandler = () => {};
 export let prod_id;

</script>



<style>
	:global(body) {
		background-color: #f2eee2;
		color: #0084f6;
		transition: background-color 0.3s
	}
	:global(body.dark-mode) {
		background-color: #1d3040;
		color: #bfc2c7;
	}
</style>

<div class="container-fluid">
    <div class="row">
        <div class="col">
            <!-- Start: Basic Card -->
            <div class="card shadow mb-4">
                <div class="card-header py-3">
                    <h6 class="text-primary m-0 font-weight-bold">Prize</h6>
                </div>
                <div class="card-body">
                    <p class="m-0"> </p>

 {#if {numberWins}> "0" }
    <h2 style="color:orange"> Congrats, you have won {numberWins} x Cumulus Points!</h2>
{:else}
    <h3 style="color:orange">Nice try! Try your luck with some other hidden products to win Cumulus Points!</h3>
  {/if}
             
            <a class="nav-link" href="./anim">
            <button> OK </button></a>
            </div>
            </div>
            <!-- End: Basic Card -->
        </div>
    </div>
</div>

