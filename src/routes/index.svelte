<script>
  import Header from '../components/Header.svelte';
  import Footer from '../components/Footer.svelte';
  import SignupForm from '../components/SignupForm.svelte';
  import TopographicBackground from '../components/TopographicBackground.svelte';

  const navItems = [
    { name: 'Home', href: '/', isActive: true },
    { name: 'Aegis', href: '/aegis', isActive: false },
    { name: 'Mission', href: '/mission', isActive: false },
  ];
</script>

<Header {navItems} />

<TopographicBackground />

<main>
  <section class="hero">
    <h1>Shielding Families with Tomorrow's Defense</h1>
    <p>Discover cutting-edge solutions for civilian safety.</p>
  </section>

  <section>
    <SignupForm />
  </section>
</main>

<Footer />

<style>

  main {
    text-align: center;
    padding: 2rem;
    z-index: 1;
    background: transparent; /* Transparent background to show the topographic background */
    color: #fff; /* White text for contrast */
    height: 80vh;
  }

  .hero {
    margin: 2rem 0;
  }

  .hero h1 {
    font-size: 2.5rem;
    font-weight: bold;
    color: #fff; /* Explicit white text for the hero heading */
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.8); /* Optional text shadow for better readability */
  }

  .hero p {
    font-size: 1.2rem;
    margin: 1rem 0;
    color: #fff; /* Explicit white text for the hero paragraph */
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.8); /* Optional text shadow for better readability */
  }

  section {
    margin: 2rem 0;
  }

  Footer {
    background: transparent; /* Ensure the footer doesn't block the background */
    color: #fff; /* White footer text for contrast */
  }

  Header {
    background: transparent; /* Ensure the header doesn't block the background */
    color: #fff; /* White header text for contrast */
  }
</style>

