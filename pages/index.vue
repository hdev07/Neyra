<template>
  <div class="main-wrap">
    <Navbar/>
    <div class="container-wrap">
      <section id="Home">
        <Home/>
      </section>
      <section id="Services">
        <Services/>
      </section>
      <section id="Products">
        <Products/>
      </section>
      <section id="FAQ">
        <FAQ/>
      </section>
      <section id="Contact-us">
        <Contact/>
      </section>
    </div>
  </div>
</template>

<script>
import Navbar from "../components/Navbar/Navbar.vue";
import Home from "../components/Home/Home.vue";
import Services from "../components/Services/Services.vue";
import Products from "../components/Products/Products.vue";
import FAQ from "../components/FAQ/FAQ.vue";
import Contact from "../components/Contact/contact.vue";
export default {
  name: "IndexPage",
  components: { Navbar, Home, Services, Products, FAQ, Contact }
}
</script>
