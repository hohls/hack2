
 <script>
	import { fade } from 'svelte/transition';
	import { elasticOut } from 'svelte/easing';

	let visible = true;

	function spin(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = elasticOut(t);

				return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${~~(t * 360)},
						${Math.min(100, 1000 - 1000 * t)}%,
						${Math.min(50, 500 - 500 * t)}%
					);`
			}
		};
	}
</script>

<style>
	.centered {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%,-50%);
	}

	span {
		position: absolute;
		transform: translate(-50%,-50%);
		font-size: 4em;
    }

    .btn-bot {
        position: absolute;
    left: 50%;
    width: 100px;
    margin-left: -50px;
    bottom:120px;

    }
    
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

	<div class="centered" in:spin="{{duration: 8000}}" out:fade>
		<span>Animation!</span>
    </div>
    
    <a class="nav-link" href="./quiz">
        <button class='btn-bot'>Ask Me! </button></a>





