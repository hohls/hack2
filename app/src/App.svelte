<script>
  import './styles.scss';
  import { Router, Link, Route } from 'svelte-routing';
import { slide } from 'svelte/transition';
  import Home from './Home.svelte';

  import { NavBar, SideBar, PageNotFound, Redirect } from './components';
  import {
    Scanner,
    ProductQuiz,
    Anim,
    Prize,
  } from './components';
  

  export let url = '';

  let showScanner = true;
  let showAnim = false;
  let showProductQuiz = false;
  let showPrize = false;

  let prod_id_gl;
let win ;



 
 function closeAnim(event) {
   showScanner = false;
  showAnim = false; 
  showProductQuiz=true };
 

	function handleId(event) {
		prod_id_gl = event.detail.text;
    showScanner = false; showAnim=true
    };

	function handleWin(event) {
		win = event.detail.text;
   showScanner = false; 
   showProductQuiz = false; 
   showPrize=true
    }

</script>

<Router {url}>
 

<div class="container">
  {#if showScanner}
    <div transition:slide|local>
      <Scanner on:message={handleId} />
    </div>
  {/if}

  {#if showAnim}
    <div transition:slide|local>
      <Anim on:message={closeAnim} prod_id=prod_id_gl />
    </div>
  {/if}

  {#if showProductQuiz}
    <div transition:slide|local>
      <ProductQuiz on:message={handleWin} prod_id=prod_id_gl  />
    </div>
  {/if}

   {#if showPrize}
    <div transition:slide|local>
      <Prize />
    </div>
  {/if}


</div>


</Router>
