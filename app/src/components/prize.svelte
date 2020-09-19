
 <script>
	import Button from './Button.svelte'
	let question = 'hole von json';
  let a1 = "OK"
  import API from '../store/config';
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
           <h2>Congrats, you have won </h2>
            <h2> </h2>
            <a class="nav-link" href="./anim">
            <button> OK </button></a>
            </div>
            </div>
            <!-- End: Basic Card -->
        </div>
    </div>
</div>

