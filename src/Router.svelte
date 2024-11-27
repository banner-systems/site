<script>
  import { Router, Route, Link } from "svelte-routing";
  import index from "./routes/index.svelte";
  import aegis from "./routes/aegis.svelte";
  import mission from "./routes/mission.svelte";
</script>

<Router>
  <Route path="/" component={index} />
  <Route path="/about" component={aegis} />
  <Route path="/mission" component={mission} />
</Router>

