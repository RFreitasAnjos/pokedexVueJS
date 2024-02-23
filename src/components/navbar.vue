
import { RouterLink } from 'vue-router';
<template>
    <nav class="navbar" role="navigation" aria-label="main navigation">
  <div class="navbar-brand">
    <a class="navbar-item" href="/">
      <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28">
    </a>

    <a role="button" class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
      <span aria-hidden="true"></span>
    </a>
  </div>

  <div id="navbarBasicExample" class="navbar-menu">
    <div class="navbar-start">
      <RouterLink to="/" class="navbar-item">
        Primeira Geracao
      </RouterLink>

      <RouterLink to="/geracao2" class="navbar-item">
        Segunda Geracao
      </RouterLink>

      <RouterLink to="/geracao3" class="navbar-item">
        Terceira Geracao
      </RouterLink>
      
    </div>

  </div>
</nav>
</template>