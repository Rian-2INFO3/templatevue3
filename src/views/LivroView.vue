<template>
  <div>
    <header>
      <h1 class="welcome" align="center">Saiba Mais</h1>
      <a class="inicio" href="App.vue">Home</a>
      <a align="right" class="info3" href="Objetivos e Benefícios.html">Objetivos e Benefícios</a>
    </header>
    
    <section id="welcome">
      <h2 align="center">Bem-vindo ao nosso Refeitório</h2>
      <p style="text-align: center;">
        Nosso refeitório oferece uma variedade de pratos saudáveis e deliciosos,<br>
        preparados com ingredientes frescos e de qualidade. <br>
        Venha experimentar nossas opções!
      </p>
    </section>
    <section style="text-align: center;" id="menu">
      <h2>Cardápio</h2>
      <ul>
        <li v-for="(item, index) in menuItems" :key="index">{{ item }}</li>
      </ul>
    </section>
    <section style="text-align: center;" id="hours">
      <h2>Horários de Funcionamento</h2>
      <p v-for="(hour, index) in hours" :key="index">{{ hour }}</p>
    </section>
    <section style="text-align: center;" id="contact">
      <h2>Contato</h2>
      <p>
        Se você tiver dúvidas ou sugestões, entre em contato conosco pelo e-mail: 
        <a href="mailto:contato@refeitorioif.edu.br">contato@refeitorioif.edu.br</a>
      </p>
    </section>
    <footer>
      <p>&copy; 2024 Refeitório. Todos os direitos reservados.</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuItems: [
        "Saladas frescas",
        "Pratos principais (carne, peixe, opções vegetarianas)",
        "Sobremesas",
        "Bebidas variadas"
      ],
      hours: [
        "Segunda a Sexta: 11h às 14h",
        "Sábado: Fechado",
        "Domingo: Fechado"
      ]
    };
  }
};
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

header {
  background-color: #4caf50;
  color: white;
  padding: 1em 0;
  text-align: center;
}

nav {
  margin: 0;
  padding: 0;
  text-align: center;
  background-color: #333;
}

nav a {
  color: white;
  padding: 14px 20px;
  text-decoration: none;
  display: inline-block;
}

nav a:hover {
  background-color: #ddd;
  color: black;
}

section {
  padding: 20px;
  margin: 10px;
  background-color: white;
  border-radius: 5px;
}

footer {
  text-align: center;
  padding: 10px;
  background-color: #333;
  color: white;
  position: fixed;
  bottom: 0;
  width: 100%;
}

.header-link {
  position: absolute;
  top: 10px;
  right: 20px;
  color: white;
  text-decoration: none;
  font-weight: bold;
}

.header-link:hover {
  text-decoration: underline;
}

li {
  list-style: none;
}

.welcome {
  margin-right: 1%;
}

img {
  display: block;
  margin: 0 auto;
  max-width: 100%;
  height: auto;
  border-radius: 15px;
}

.div {
  text-align: center;
  margin: 20px 0;
}

.inicio, .info3 {
  position: fixed;
  top: 0;
  padding: 15px;
  text-decoration: none;
  color: white;
}

.inicio {
  right: 20px;
}

.info3 {
  left: 20px;
}

@media (max-width: 600px) {
  header {
    padding: 10px;
  }
  .inicio, .info3 {
    padding: 10px;
  }
}
</style>
