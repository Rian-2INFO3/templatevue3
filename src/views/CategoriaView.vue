<template>
  <div>
    <header>
      <div class="saiba">
       
      </div>
      <h1>Benefícios da Comida na Escola</h1>
    </header>

    <div class="container">
      <h2>Por que a comida escolar é importante?</h2>
      <div class="benefit" v-for="(benefit, index) in benefits" :key="index">
        <h3>{{ index + 1 }}. {{ benefit.title }}</h3>
        <p>{{ benefit.description }}</p>
      </div>
      <button @click="toggleExtraInfo">{{ moreInfoButtonText }}</button>
      <div class="extra-info" v-if="showExtraInfo">
        <h3>Benefícios Adicionais:</h3>
        <ul>
          <li v-for="(extra, index) in extraBenefits" :key="index">{{ extra }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      benefits: [
        { title: "Melhora a Concentração", description: "A comida saudável fornece a energia necessária para que os alunos se mantenham concentrados durante as aulas." },
        { title: "Estimula o Crescimento", description: "Uma alimentação balanceada é essencial para o crescimento e desenvolvimento adequado das crianças." },
        { title: "Promove Hábitos Saudáveis", description: "A escola é um ótimo lugar para ensinar os alunos sobre a importância de uma alimentação saudável." },
        { title: "Aumenta a Sociabilidade", description: "As refeições em grupo incentivam a interação social e ajudam a construir amizades." }
      ],
      extraBenefits: [
        "Redução do estresse e da ansiedade.",
        "Melhora na performance acadêmica.",
        "Redução de doenças relacionadas à má alimentação."
      ],
      showExtraInfo: false
    };
  },
  computed: {
    moreInfoButtonText() {
      return this.showExtraInfo ? "Ocultar informações adicionais" : "Saiba mais sobre os benefícios";
    }
  },
  methods: {
    toggleExtraInfo() {
      this.showExtraInfo = !this.showExtraInfo;
    }
  }
};
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #000000;
  color: #333;
}
header {
  background-color: #4CAF50;
  color: white;
  padding: 15px;
  text-align: center;
}
.container {
  width: 90%;
  max-width: 800px;
  margin: 20px auto;
  background: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}
h2 {
  color: #4CAF50;
}
.benefit {
  margin: 15px 0;
  padding: 10px;
  border: 1px solid #000000;
  border-radius: 5px;
  background-color: #e7f9e7;
}
button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}
button:hover {
  background-color: #45a049;
}
.extra-info {
  margin-top: 10px;
  padding: 10px;
  background-color: #f9f9f9;
  border: 1px solid #ccc;
  border-radius: 5px;
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
.link-topo-esquerda, .inicio {
  position: fixed;
  top: 0;
  padding: 15px;
  text-decoration: none;
  color: white;
}
.link-topo-esquerda {
  left: 20px;
}
.inicio {
  right: 20px;
}
@media (max-width: 600px) {
  header {
    padding: 10px;
  }
  .container {
    width: 95%;
    padding: 15px;
  }
  .link-topo-esquerda, .inicio {
    padding: 10px;
  }
}
</style>
