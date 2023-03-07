<script>
</script>

<template>
  <header>
    <nav class="container">
      <div class="nav_items">
        <ul>
          <RouterLink ref="home" to="/">Inicio</RouterLink>
          <li><a href="#">Contacto</a></li>
          <div class="nav_title">
            <img
              id="nav_image"
              src="../../public/PngItem_3542954.png"
              alt="travel header icon"
            />
            <h1>Viajes Bernal</h1>
          </div>
          <li><a href="#">Nosotros</a></li>
          <li><a href="#">Blog</a></li>
        </ul>
      </div>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
@import "../styles/variables";
header {
  background-color: $gray;
  height: 7rem;
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-family: $poppins;
    font-size: 1.5rem;
    height: 7rem;
    padding-top: .3rem;
    .nav_title {
      margin-top: -5px;
      padding-left: 2rem;
      display: flex;
      align-items: center;
      width: 22%;
      color: $dark-text;
      #nav_image {
        filter: invert(25%);
        width: 12%;
        margin-right: 1rem;
      }
    }

    .nav_items > ul {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 2rem;
      list-style: none;
      a {
        font-size: 1.2rem;
        text-decoration: none;
        color: $dark-text;
        font-weight: 400;
        &:hover {
          transition: 0.8s;
        }
      }
    }
  }
}
</style>