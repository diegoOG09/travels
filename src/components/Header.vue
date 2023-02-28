<template>
  <header>
    <nav class="container">
      <div class="nav_title">
        <img
          id="nav_image"
          src="../../public/PngItem_3542954.png"
          alt="travel header icon"
        />
        <h1>Viajes Bernal</h1>
      </div>
      <div class="nav_items">
        <ul>
          <li><a href="#">Inicio</a></li>
          <li><a href="#">Viajar</a></li>
          <li><a href="#">Contacto</a></li>
          <li><a href="#">Nosotros</a></li>
          <li><a href="#">Blog</a></li>
        </ul>
      </div>
      <div class="nav_login">
        <a href="#">Iniciar sesión</a>
      </div>
    </nav>
  </header>
</template>

<script>
</script>

<style lang="scss" scoped>
@import "../styles/variables";
header {
  backdrop-filter: blur(5px);
  margin-bottom: 4rem;
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-family: $montserrat;
    font-size: 1.5rem;
    padding: 2rem 0 0 0;

    .nav_title {
      margin-top: -5px;
      padding-left: 2rem;
      display: flex;
      align-items: center;
      width: 22%;
      color: $white;
      #nav_image {
        filter: invert(95%);
        width: 12%;
        margin-right: 1rem;
      }
    }

    .nav_items > ul {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 2.5rem;
      list-style: none;
      padding: 0;
      a {
        font-size: 1.4rem;
        text-decoration: none;
        text-shadow: 2px 1px 2px rgba(0, 0, 0, 0.6);
        color: white;
        font-weight: 500;
        &:hover {
          transition: 0.8s;
        }
      }
    }
    .nav_login {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 1.5rem;
      a {
        font-weight: 600;
        text-decoration: none;
        color: white;
        text-shadow: 2px 1px 2px rgba(0, 0, 0, 0.6);
      }
      #sign_up {
        background-color: $green;
        text-shadow: none;
        padding: 1rem 1rem;
        border-radius: 8px;
        color: $white;
        box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px, rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
        &:hover {
          box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
        }
      }
    }
  }
}
</style>