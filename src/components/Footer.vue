<script>
</script>

<template>
  <footer id="footer" class="footer">
    <div class="container">
      <ul>
        <li><RouterLink ref="home" to="/">Inicio</RouterLink></li>
        <li><a href="#">Contacto</a></li>
        <li><a href="#">Nosotros</a></li>
        <li><a href="#">Blog</a></li>
        </ul>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
@import "../styles/variables";
.footer {
  margin-top: auto;
  background-color: $sand;
  ul {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 2rem;
    margin: 0;
    height: 8rem;
    li {
      list-style: none;
      a {
        text-decoration: none;
        color: $dark-text;
        font-family: $poppins;
      }
    }
  }
}
</style>