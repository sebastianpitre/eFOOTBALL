<script>
  import { Router, Route} from "svelte-routing";
  import Home from "./routes/Home.svelte";
  import Login from "./components/Login.svelte";
    import Efootball from "./Efootball.svelte";
    import FullScreen from "./components/FullScreen.svelte";
</script>

<main>
  <FullScreen />
  <Router>
    <Route path="/" component={Efootball} exact />
    <Route path="/login" component={Login} />
    <Route path="/home" component={Home} />
  </Router>
</main>
