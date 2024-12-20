<template>
  <header>
  <nav>
      

      <div class="nav-right" v-if="isLoggedIn">
        <!-- Link para o perfil alinhado à esquerda -->
        <router-link to="/usuario" class="profile-link">Perfil</router-link>

        <!-- Foto do usuário com dropdown -->
        <div class="user-menu" @click="toggleDropdown">
          <img
            v-if="user.foto && user.foto.url"
            :src="user.foto.url"
            alt="Foto do usuário"
            class="user-photo-small"
          />
          <img
            v-else
            src="https://via.placeholder.com/50"
            alt="Sem foto"
            class="user-photo-small"
          />

          <div v-if="showDropdown" class="dropdown-menu">
            <p><strong>{{ user.name }}</strong></p>
            <p class="email">{{ user.email }}</p> <!-- Adiciona classe email -->
            <router-link to="/logout" class="dropdown-item">Logout</router-link>
         
         
          </div>
        </div>
      </div>


      <table class="menu-table">
      <thead>
        <tr>
          <th>Dia</th>
          <th>Prato Principal</th>
          <th>Acompanhamentos</th>
          <th>Sobremesa</th>
          <th>Sem Glúten</th>
          <th>Vegetariano</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in filteredMenu" :key="index">
          <td>{{ item.dia }}</td>
          <td>{{ item.prato }}</td>
          <td>{{ item.acompanhamentos }}</td>
          <td>{{ item.sobremesa }}</td>
          <td>{{ item.semGluten ? 'Sim' : 'Não' }}</td>
          <td>{{ item.vegetariano ? 'Sim' : 'Não' }}</td>
        </tr>
      </tbody>
    </table>

      
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      filters: {
        semGluten: false,
        vegetariano: false,
      },
      menu: [
        {
          dia: 'Segunda-feira',
          prato: 'Frango Assado',
          acompanhamentos: 'Arroz, Feijão, Salada',
          sobremesa: 'Fruta',
          semGluten: true,
          vegetariano: false,
        },
        {
          dia: 'Terça-feira',
          prato: 'Iscas de Frango empanado',
          acompanhamentos: 'Arroz, Feijão, Alface',
sobremesa: 'Banana',
semGluten: true,
vegetariano: false,

        },
        {
          dia: 'Quarta-feira',
          prato: 'Peixe Grelhado',
          acompanhamentos: 'Arroz Integral, Legumes',
          sobremesa: 'Gelatina',
          semGluten: true,
          vegetariano: false,
        },
        {
          dia: 'Quinta-feira',
          prato: 'Carne de Panela',
          acompanhamentos: 'Purê de Batata, Salada',
          sobremesa: 'Sorvete',
          semGluten: true,
          vegetariano: false,
        },
        {
          dia: 'Sexta-feira',
          prato: 'Pizza Vegetariana',
          acompanhamentos: 'Salada Completa',
          sobremesa: 'Bolo',
          semGluten: false,
          vegetariano: true,
        },
      ],
    }
  },
  computed: {
    filteredMenu() {
      return this.menu.filter(item => {
        return (
          (!this.filters.semGluten || item.semGluten) &&
          (!this.filters.vegetariano || item.vegetariano)
        )
      })
    },
  },
}
</script>





<style scoped>
/* Estilos gerais da barra de navegação */
.navbar {
  background-color: #16c510;
  color: #00ff00;
  padding: 15px 20px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-left {
  display: flex;
  align-items: center;
}

.nav-left a {
  color: #12f812;
  text-decoration: none;
  margin-right: 20px;
  font-weight: bold;
}

.logo {
  font-size: 1.5rem;
}

.nav-right {
  display: flex;
  align-items: center;
}

.profile-link {
  color: #fff;
  text-decoration: none;
  margin-right: 15px;
  font-weight: bold;
}

.user-menu {
  position: relative;
  cursor: pointer;
}

.user-photo-small {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  object-fit: cover;
  border: 2px solid #fff;
  transition: border-color 0.3s;
}

.user-photo-small:hover {
  border-color: #4a90e2;
}

/* Dropdown menu */
.dropdown-menu {
  position: absolute;
  top: 50px;
  right: 0;
  background-color: #fff;
  color: #333;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
  white-space: nowrap;
  z-index: 1000;
  min-width: 200px; /* Define um tamanho mínimo para o dropdown */
}

.dropdown-menu p {
  margin: 0;
  padding: 5px 0;
}

.dropdown-item {
  display: block;
  color: #333;
  text-decoration: none;
  padding: 8px;
  border-radius: 4px;
  transition: background-color 0.2s;
}

.dropdown-item:hover {
  background-color: #f4f4f4;
}

/* Estilo específico para o email */
.email {
  word-wrap: break-word; /* Garante que o e-mail quebre de forma adequada se for longo */
  font-size: 0.9rem;
  color: #666;
  margin-bottom: 10px;
}

/* Estilos do botão de login */
.login-btn {
  background-color: #555;
  padding: 10px 20px;
  color: white;
  border-radius: 5px;
  text-decoration: none;
  transition: background-color 0.3s;
}

.login-btn:hover {
  background-color: #000;
}

/* Responsividade */
@media (max-width: 600px) {
  .navbar {
    padding: 10px;
  }

  .nav-left a {
    margin-right: 10px;
  }

  .user-photo-small {
    width: 35px;
    height: 35px;
  }
}

/* * {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #f4f4f4;
  min-height: 100vh;
  font-family: Arial, sans-serif;
} */

.logo {
  display: flex;
  align-items: center;
}

.container {
  width: 100%;
  background-color: #fff;
  padding: 200px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  text-align: center;
}

h1 {
  font-size: 32px;
  margin-bottom: 35px;
  color: #333;
}

.filters {
  margin-bottom: 15px;
  display: flex;
  gap: 10px;
  justify-content: center;
}

.filters label {
  font-size: 16px;
  color: #333;
}

.menu-table {
  width: 100%;
  border-collapse: collapse;
}

.menu-table th,
.menu-table td {
  padding: 12px;
  border: 1px solid #ddd;
}

.menu-table th {
  background-color: #4caf50;
  color: white;
}

@media (max-width: 600px) {

  .menu-table th,
  .menu-table td {
    padding: 8px;
    font-size: 14px;
  }
}
</style>

    