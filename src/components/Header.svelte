<script>
  import { Router, Route, Link } from "svelte-routing";
  export let navItems = [];
</script>

<header class="header">
  <div class="logo">Banner Systems</div>
  <nav>
    {#each navItems as { name, href, isActive }}
      <a href={href} class:is-active={isActive}>{name}</a>
    {/each}
  </nav>
</header>

<style>

  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background: transparent; /* Transparent to show the background */
    color: #fff; /* White text for contrast */
    border-bottom: 2px solid white; /* Add a white border under the header */
  }

  .logo {
    font-size: 1.5rem;
    font-weight: bold;
    padding: 0.5rem 1rem;
    border: 2px solid white; /* Outline the logo with a white border */
    border-radius: 5px; /* Add slight rounding to the corners */
  }

  nav {
    display: flex;
    gap: 1rem; /* Add space between navigation links */
  }

  nav a {
    padding: 0.5rem 1rem;
    text-decoration: none;
    color: #fff;
    border: 2px solid white; /* Add white outline to each link */
    border-radius: 5px; /* Slight rounding for the links */
    opacity: 0.8; /* Slightly transparent links for inactive state */
    transition: all 0.3s ease-in-out; /* Smooth transitions for hover and active effects */
  }

  nav a.is-active {
    opacity: 1; /* Fully opaque for active links */
    font-weight: bold;
    background: white; /* Invert the background for active links */
    color: black;
  }

  nav a:hover {
    background: white; /* Invert colors on hover */
    color: black;
  }
</style>

