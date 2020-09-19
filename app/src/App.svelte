<script>
  import './styles.scss';
  import { Router, Link, Route } from 'svelte-routing';

  import Home from './Home.svelte';

  import { NavBar, SideBar, PageNotFound, Redirect } from './components';
  import {
    MigrosData,
    MigrosProductSearch,
    CustomVision,
    FormRecognizer,
    Chatbot,
    BingMaps,
    SpatialAnchors,
    Scanner,
    ProductQuiz,
    Anim,
    Prize,
  } from './components';
  import Animation from './components/animation.svelte';

  export let url = '';
</script>

<Router {url}>
  <!-- The left side -->
  <SideBar />

  <!-- The main content area -->
  <div class="d-flex flex-column" id="content-wrapper">
    <div id="content">
      <!-- The top navbar -->
      <NavBar />

      <!-- Content area -->
      <div class="container-fluid">
        <Route path="/">
          <Redirect path="/home" />
        </Route>
        <Route path="/home" component={Home} />

        <Route path="/scanner" component={Scanner} />
        <Route path="/data" component={MigrosData} />
        <Route path="/customvision" component={CustomVision} />
        <Route path="/formrecognizer" component={FormRecognizer} />
        <Route path="/chatbot" component={Chatbot} />
        <Route path="/maps" component={BingMaps} />
        <Route path="/spatialanchors" component={SpatialAnchors} />
        <Route path="/quiz" component={ProductQuiz} />
        <Route path="/anim" component={Anim} />
        <Route path="/prize" component={Prize} />

        <Route path="/productsearch" component={MigrosProductSearch} />

        <!--
          <Route path="/scandit" component={Scandit} />
        -->

        <Route path="**" component={PageNotFound} />
      </div>
    </div>
  </div>
</Router>
