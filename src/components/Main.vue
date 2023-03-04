<template>
  <main>
    <h2 class="main_text container">
      Viaja con nosotros y recorre los lugares más hermosos de México
    </h2>
    <p class="main_paragraph container">
      México es un país bellísimo y con una diversidad inmensa tanto de fauna,
      flora y ecosistemas, incluyendo vistas hermosas de playas, montañas,
      desiertos y más. Es por eso que nos dedicamos a recorrer algunos de los
      lugares más famosos de dicho país.
    </p>
    <a class="container" id="main_button" href="#">Apartar un lugar</a>
  </main>
</template>

<script>
</script>

<style lang="scss" scoped>
@import "../styles/variables";
main {
  padding-bottom: 10rem;
  padding-top: 3rem;
  background-image: linear-gradient(to bottom, #003268, #004f81, #006c8d, #00878d, #16a085);
  .main_text {
    line-height: 5.5rem;
    margin-bottom: 3rem;
    padding-top: 10rem;
    width: 75%;
    color: $white;
    font-family: $montserrat;
    font-size: 4rem;
    font-weight: 700;
    text-align: center;
    text-shadow: 2px 1px 2px rgba(0, 0, 0, 0.6);
    letter-spacing: 1px;
  }
  .main_paragraph {
    line-height: 2.5rem;
    text-align: center;
    width: 60%;
    color: $white;
    font-family: $montserrat;
    font-size: 1.8rem;
    font-weight: 400;
    margin-bottom: 3rem;
  }
  #main_button {
    font-weight: 700;
    font-size: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 15rem;
    color: $white;
    text-decoration: none;
    font-family: $montserrat;
    background-color: $green;
    padding: 1rem 2.5rem;
    border-radius: 8px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    &:hover {
      box-shadow: rgba(50, 50, 93, 0.25) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
    }
  }
}
</style>