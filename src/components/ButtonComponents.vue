<template>
  <div>
    <router-link v-if="to" :to="to" :class="['btn', buttonTypeClass]">
      <i v-if="icon" :class="icon"></i>
      {{ label }}
    </router-link>

    <button v-else :class="['btn', buttonTypeClass]">
      <i v-if="icon" :class="icon"></i>
      {{ label }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'ButtonComponent',
  props: {
    label: {
      type: String,
      required: true
    },
    type: {
      type: String,
      default: 'default'
    },
    // to: {
    //   type: String,
    //   default: '/'
    // },
    icon: {
      type: String,
      default: 'default'
    },
  },
  computed: {
    buttonTypeClass() {
      switch (this.type) {
        case 'logout':
          return 'btn-logout';
        case 'register':
          return 'btn-register';
        case 'login':
          return 'btn-login';
        case 'submit':
          return 'btn-submit';
        case 'add':
          return 'btn-add';
        case 'delete':
          return 'btn-delete';
        case 'trash':
          return 'btn-trash';
        default:
          return 'btn-default';
      }
    }
  },
}
</script>

<style scoped>
.btn {
  min-width: 8rem;
  padding: clamp(0.6rem, 0.7vw, 0.8rem);
  /* font-size: 1rem; */
  font-size: clamp(0.7rem, 1rem, 1.5rem);
  font-weight: bold;
  cursor: pointer;
  border-radius: 5px;
  text-decoration: none;
  /* margin: 2rem; */
}

.btn:hover {
  transition: 0.3s ease;
  background-color: transparent;
}

.btn-logout {
  /* logout */
  background-color: var(--color-logout);
  color: var(--color-background);
  border: 2px solid var(--color-logout);
}

.btn-logout:hover {
  /* logout:hover */
  color: var(--color-logout);
  border: 2px solid var(--color-logout);
}

.btn-register {
  /* register */
  background-color: var(--color-accent);
  color: var(--color-secondary);
  border: 2px solid var(--color-accent);
}

.btn-register:hover {
  /* register:hover */
  color: var(--color-accent);
  border: 2px solid var(--color-accent);
}

.btn-login {
  /* login */
  background-color: var(--color-secondary);
  color: var(--color-background);
  border: 2px solid var(--color-secondary);
}

.btn-login:hover {
  /* login:hover */
  color: var(--color-secondary);
  border: 2px solid var(--color-secondary);
}
.btn-add {
  /* login */
  background-color: var(--color-secondary);
  color: var(--color-background);
  border: 2px solid var(--color-secondary);
  padding: 0.1rem;
}

.btn-add:hover {
  /* login:hover */
  color: var(--color-secondary);
  border: 2px solid var(--color-secondary);
}
.btn-delete {
  /* login */
  background-color: var(--color-logout);
  color: var(--color-background);
  border: 2px solid var(--color-logout);
  padding: 0.2rem;
}

.btn-delete:hover {
  /* login:hover */
  color: var(--color-logout);
  border: 2px solid var(--color-logout);
}

.btn-submit {
  /* submit */
  background-color: var(--color-secondary);
  color: var(--color-background);
  border: 2px solid var(--color-secondary);
  padding: 1rem 2rem;
  font-size: 1rem;
  border-radius: 50px;
  cursor: pointer;
  width: 100%;
}

.btn-submit:hover {
  /* submit:hover */
  border: 2px solid var(--color-secondary);
  color: var(--color-secondary);
}

/* Default) */
.btn-default {
  background-color: #6c757d;
  color: var(--color-background);
}

.btn-default:hover {
  background-color: var(--color-background);
  color: #6c757d;
}
</style>
