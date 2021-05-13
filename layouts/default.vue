<template>
  <main>
    <header>
      <h3>Hello! 👋</h3>
      <h1 class="welcome-line">Welcome to my blog 📢</h1>
    </header>
    <Nuxt />
  </main>
</template>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
main {
  max-width: 500px;
  margin: 1rem auto;
  font-family: 'Inconsolata', monospace;
}
.welcome-line {
  font-size: 2.5rem;
}
a,
a:visited {
  text-decoration: none;
  color: rgb(24, 140, 207);
}

a:hover {
  color: rgb(37, 93, 167);
}
@media only screen and (max-width: 600px) {
  main {
    margin: 1.5rem;
  }
}
</style>
