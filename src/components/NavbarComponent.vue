<template>
  <nav class="navbar navbar-expand-md navbar-light bg-light">
    <a class="navbar-brand" href="#">
      <img src="../assets/logo.png" width="120" height="40" alt />
    </a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>

    <div class="collapse navbar-collapse ml-auto" id="navbarSupportedContent">
      <ul class="navbar-nav">
        <li class="nav-item active pl-4">
          <a class="nav-link" href="#">Tee Shirts</a>
        </li>
      </ul>
      <form class="form-inline pr-3 ml-auto">
        <input class="form-control mr-1" type="search" placeholder="Search" aria-label="Search" />
        <button class="btn btn-sm btn-outline-success my-2 my-sm-0" type="submit">Search</button>
      </form>
    </div>
  </nav>
</template>

<script>
export default {};
</script>

<style>
</style>