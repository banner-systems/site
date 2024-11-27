<script>
  import Header from '../components/Header.svelte';
  import Footer from '../components/Footer.svelte';
</script>

<Header navItems={[{ name: 'Aegis', href: '/aegis', isActive: true }]} />

<main>
  <h1>Aegis</h1>
  <p>Details about Aegis will go here.</p>
</main>

<Footer />

<style>
  main {
    text-align: center;
    padding: 2rem;
  }
</style>

