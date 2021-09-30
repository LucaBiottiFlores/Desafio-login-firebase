<template>
  <div>
    <b-container>
        <b-card>
      <b-form  @submit.prevent="submitForm">
        <b-form-group 
          label="Email:"
          label-for="email"
        >
          <b-form-input
            class="colorInput"
            id="email"
            type="email"
            placeholder="Ingrese Correo Electrónico"
            required
            v-model="email"
          ></b-form-input>
        </b-form-group>

        <b-form-group  label="Password" label-for="password">
          <b-form-input
           class="colorInput"
            id="password"
            type="password"
            placeholder="Ingrese Contraseña"
            required
            v-model="password"
          ></b-form-input>
        </b-form-group>

        <b-button class="colorBtn" type="submit" variant="primary">Submit</b-button>
      </b-form>
        </b-card>
    </b-container>
  </div>
</template>

<script>
import Firebase from 'firebase'
export default {
  data: () => ({
    email: '',
    password: ''
  }),
  // submitForm es un metodo creado para usar el autenticador de Firebase, funciona como un llamado asíncrono
  // por lo que tiene sintaxis de promesa.
  // Basicamente toma los valores de los input para revisar si son válidos en Firebase.
  methods: {
    submitForm() {
      Firebase.auth()
        .signInWithEmailAndPassword(this.email, this.password)
        .then((response) => {
          console.log(response.user.email)
          this.$store.dispatch('defineCurrentUser', {email: response.user.email})
          this.$router.push('/')
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>

<style>
.card {
background: rgba( 255, 255, 255, 0.25 );
box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
backdrop-filter: blur( 20px );
-webkit-backdrop-filter: blur( 20px );
border-radius: 10px;
border: 1px solid rgba( 255, 255, 255, 0.18 );
}
.colorInput {
   background: rgba(233, 197, 106, 0.671);
box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
backdrop-filter: blur( 20px );
-webkit-backdrop-filter: blur( 20px );
border-radius: 10px;
border: 1px solid rgba( 255, 255, 255, 0.18 );
}
.colorBtn {
    background: rgba(231, 111, 81, 0.719);
box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
backdrop-filter: blur( 20px );
-webkit-backdrop-filter: blur( 20px );
border-radius: 10px;
border: 1px solid rgba( 255, 255, 255, 0.18 );
}
</style>
