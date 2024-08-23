<template>
  
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons/font/bootstrap-icons.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">

  <div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-info fixed-top">
      <div class="container-fluid">
        <router-link to="/" class="navbar-brand d-flex align-items-center">
          <i class="fas fa-book me-2"></i> <!-- Brand icon -->
          <strong>GestionPro</strong>
        </router-link>
  
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarTogglerDemo02"
          aria-controls="navbarTogglerDemo02"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <i class="fas fa-bars"></i>
        </button>
  
        <div class="collapse navbar-collapse" id="navbarTogglerDemo02">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <router-link
                to="/taches"
                class="nav-link"
                active-class="active"
                aria-current="page"
              >
                <i class="fas fa-tasks me-2"></i> Tâches
              </router-link>
            </li>
            <li class="nav-item">
              <router-link
                to="/projets"
                class="nav-link"
                active-class="active"
              >
                <i class="fas fa-project-diagram me-2"></i> Projets
              </router-link>
            </li>
          </ul>
  
          <form class="d-flex input-group w-auto me-3">
            <input
              type="search"
              class="form-control"
              placeholder="Rechercher"
              aria-label="Search"
            />
            <button
              class="btn btn-outline-light"
              type="button"
            >
              <i class="fas fa-search"></i>
            </button>
          </form>
  
          <ul class="navbar-nav d-flex flex-row">
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle text-white"
                href="#"
                id="navbarDropdown"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                <i class="fas fa-user"></i>
              </a>
              <ul class="dropdown-menu dropdown-menu-end" aria-labelledby="navbarDropdown">
                <li><router-link to="/profile" class="dropdown-item">Mon compte</router-link></li>
                <li><a class="dropdown-item" href="#">Déconnexion</a></li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <div class="navbar-spacer"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
</script>

<style scoped>
.navbar {
  background-color: #17a2b8;
  padding: 0.5rem 1rem;
  z-index: 1000;
}

.fixed-top {
  position: fixed;
  top: 0;
  width: 100%;
}

.navbar-brand {
  font-size: 1.25rem;
  font-weight: bold;
}

.navbar-brand i {
  font-size: 1.5rem;
}

.nav-link {
  font-size: 1rem;
  font-weight: bold;
}

.nav-link i {
  font-size: 1.25rem;
}

.btn-outline-light {
  color: #ffffff;
  border-color: #ffffff;
}

.btn-outline-light:hover {
  background-color: #ffffff;
  color: #17a2b8;
}

.navbar-spacer {
  height: 70px;
}

.dropdown-menu {
  border-radius: 0.5rem;
}

@media (max-width: 992px) {
  .navbar-collapse {
    background-color: #17a2b8;
  }
  
  .navbar-nav .nav-link {
    font-size: 1rem;
  }
  
  .navbar-brand {
    font-size: 1.125rem;
  }
  
  .navbar-brand i {
    font-size: 1.25rem;
  }
}
</style>
