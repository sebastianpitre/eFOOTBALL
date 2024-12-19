<script>
  import { Router, Route} from "svelte-routing";
  import Home from "./routes/Home.svelte";
  import Login from "./Login.svelte";
</script>

<main>
  <Router>
    <Route path="/" component={Login} exact />
    <Route path="/home" component={Home} />
  </Router>
</main>
