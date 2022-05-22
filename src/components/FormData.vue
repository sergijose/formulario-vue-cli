<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6">
        <div class="card card-primary">
          <div class="card-header">
            <h3 class="card-title">
              <font style="vertical-align: inherit"
                ><font style="vertical-align: inherit">Formulario</font></font
              >
            </h3>
          </div>

          <form id="app" @submit.prevent="validarForm" action="#" method="post">
            <div class="card-body">
              <div class="alert alert-danger" role="alert" v-if="errors.length > 0">
                <ul class="text-danger fw-bold">
                  <li v-for="error in errors" v-bind:key="error.index">
                    {{ error }}
                  </li>
                </ul>
              </div>

              <div v-else class="text-success">
                <strong> </strong>
              </div>

              <!--nombre-->
              <div class="form-group">
                <label for="nombre">Nombre completo</label>
                <input
                  :class="{ invalido: !usuario.nombre }"
                  type="text"
                  class="form-control"
                  id="nombre"
                  placeholder="Ingrese nombre completo"
                  v-model="usuario.nombre"
                  
                />
                <span
                  class="text success fw-bold"
                  v-for="error in errors"
                  v-bind:key="error.index"
                  >{{
                }}</span>
              </div>

              <!--email-->
              <div class="form-group">
                <label for="exampleInputEmail1"
                  >Dirección de correo electrónico></label
                >
                <input
                  type="email"
                  class="form-control"
                  id="exampleInputEmail1"
                  placeholder="Ingrese correo electrónico"
                  v-model="usuario.email"
                />
                <span class="text success fw-bold">{{ usuario.email }}</span>
              </div>

              <!--edad-->
              <div class="form-group">
                <label for="exampleInputEmail1">Edad</label>
                <input
                  type="number"
                  class="form-control"
                  id="exampleInputEmail1"
                  placeholder="Ingrese su edad"
                  v-model="usuario.edad"
                />
                <span class="text success fw-bold"></span>
              </div>

              <div class="form-group">
                <label for="exampleFormControlSelect1">Ciudad</label>
                <select
                  class="form-control"
                  id="exampleFormControlSelect1"
                  v-model="usuario.ciudad"
                >
                  <option value="">Seleccione ciudad</option>
                  <option v-for="ciudad in ciudades" :key="ciudad">
                    {{ ciudad }}
                  </option>
                </select>
                <span class="text success fw-bold">{{ usuario.ciudad }}</span>
              </div>

              <input type="submit" value="enviar" />
            </div>
          </form>
        </div>
      </div>

      <div class="col-md-6">
        <table-data :usuarios="usuario"></table-data>
      </div>
    </div>
  </div>
</template>

<script>
import TableData from "./TableData.vue";
export default {
  name: "FormData",

  components: {
    TableData,
  },
  data() {
    return {
      usuario: [
        {
          nombre: "",
          email: "",
          edad: "",
          ciudad: "",
        },
      ],
      errors: [],
      ciudades: ["lima", "ica", "ciclayo"],
    };
  },

  mounted() {},

  methods: {
    validarForm: function (e) {
      e.preventDefault();
      this.errors = [];

      if (this.usuario.nombre && this.usuario.edad && this.usuario.email) {
       this.mensaje=''
        let data = {
          nombre: this.usuario.nombre,
          edad: this.usuario.edad,
          email: this.usuario.email,
          ciudad: this.usuario.ciudad,
        };

        this.usuario.push(data);
        this.mensaje="datos guardados correctamente"
        
          this.usuario.nombre='';
         this.usuario.edad='';
        this.usuario.email='';
          this.usuario.ciudad='';
    
      } else {
        if (!this.usuario.nombre) {
          this.errors.push("El nombre es obligatorio.");
        }
        if (!this.usuario.edad) {
          this.errors.push("La edad es obligatoria.");
        }
        if (!this.usuario.email) {
          this.errors.push("escriba su correo electronico.");
        }
        if (!this.usuario.ciudad) {
          this.errors.push("elige la ciudad.");
        }
      }
    },

    
  },
};
</script>

<style lang="scss" scoped></style>
