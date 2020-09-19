 <script>
	import { fade } from 'svelte/transition';
	import { elasticOut } from 'svelte/easing';
	import { createEventDispatcher } from 'svelte';
	const dispatch = createEventDispatcher();

	let src = '../../data/test.png';



 function closeMe(){
	 
	dispatch('message', {
        text: 1
    });
  }

  export let prod_id;
  let visible = true;

  function spin(node, { duration }) {
    return {
      duration,
      css: (t) => {
        const eased = elasticOut(t);

        return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${~~(t * 360)},
						${Math.min(100, 1000 - 1000 * t)}%,
						${Math.min(50, 500 - 500 * t)}%
					);`;
      },
    };
  }
  async function fetchProduct(id) {
    let errorMessage = undefined;
    try {
      const response = await fetch(`${API}/products/search?id=${id}`);
      let product = await response.json();
      return product;
    } catch (error) {
      console.log(error);
    }
  }
  console.log(prod_id);
  fetchProduct(prod_id).then(function (json) {
    console.log(json);
  });
</script>

<style>
  .centered {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
  }

  span {
    position: absolute;
    transform: translate(-50%, -50%);
    font-size: 4em;
  }

  .btn-bot {
    position: absolute;
    left: 50%;
    width: 100px;
    margin-left: -50px;
    bottom: 120px;
  }

  :global(body) {
    background-color: #f2eee2;
    color: #0084f6;
    transition: background-color 0.3s;
  }
  :global(body.dark-mode) {
    background-color: #1d3040;
    color: #bfc2c7;
  }
</style>

<<<<<<< HEAD

<div class="container-fluid">
	<div class="centered" in:spin="{{duration: 8000}}" out:fade>
		<span>Animation!</span>
    </div>
       <div class="centered">
 		<button on:click={closeMe}>
		 Ask Me! 
		 </button>


<img src={src} alt="rivella">
 </div>

 </div>



=======
<div class="component">
  <div class="centered" in:spin={{ duration: 8000 }} out:fade>
    <span>Animation!</span>
  </div>
>>>>>>> 7ef9f0d77f2725e2ecb6ffb7420c4893e487ca32

  <button on:click={closeMe}> Ask Me! </button>
</div>
