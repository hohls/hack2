
 <script>
	import Button from './Button.svelte'
	let question = 'hole von json';
  let a1 = "a1 von json hole"
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
                    <h6 class="text-primary m-0 font-weight-bold">Animatioj</h6>
                </div>
                <div class="card-body">
                    <p class="m-0">Gif.</p>
           <h2>Question 1, {question}?</h2>
            <Button>
              {a1}
            </Button>
                </div>
            </div>
            <!-- End: Basic Card -->
        </div>
    </div>
</div>

