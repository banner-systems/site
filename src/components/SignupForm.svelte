<script>
  let email = '';
  const handleSubmit = () => {
    console.log('Email submitted:', email);
    email = '';
  };
</script>

<form on:submit|preventDefault={handleSubmit} class="signup-form">
  <input
    type="email"
    placeholder="Enter your email"
    bind:value={email}
    required
  />
  <button type="submit">Sign Up</button>
</form>

<style>
  .signup-form {
    display: flex;
    justify-content: center;
    margin: 2rem 0;
  }
  .signup-form input {
    padding: 0.5rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    margin-right: 0.5rem;
  }
  .signup-form button {
    cursor: pointer;

    font-size: 1.5rem;
    font-weight: bold;
    padding: 0.5rem 1rem;
    border: 2px solid white; /* Outline the logo with a white border */
    border-radius: 5px; /* Add slight rounding to the corners */
  }
</style>

