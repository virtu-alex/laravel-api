<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <a class="navbar-brand" href="#">Navbar</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNav"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <div class="navbar-nav">
          <a class="nav-item nav-link active" href="#"
            >Home <span class="sr-only">(current)</span></a>
        </div>
      </div>
    </nav>
  </header>
</template>
<script>
export default {
    name: "AppHeader",
    props: {
        title: String,
    },
};
</script>
<style lang="">

</style>
