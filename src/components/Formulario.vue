<script>
  export default{
    data:()=>({
      proyecto:"",
      tipo:"",
      urgente: false,
      proyectos:[],
    }),
    methods:{
      registrarProyecto()
      {
        const proyecto={
          proyecto: this.proyecto,
          tipo: this.tipo,
          urgente: this.urgente,
        };
        this.proyectos.push(proyecto);
        this.proyecto="",
        this.tipo="",
        this.urgente=false;

        console.log(this.proyectos);
      },
    },
  };
</script>


<template>
    <form @submit.prevent="registrarProyecto">
      <div class="mb-3">
        <label  class="form-label">Proyecto</label>
        <input v-model.trim="proyecto" type="text" class="form-control" required/>
      </div>


      <div class="mb-3">
        <label class="form-label">Actividad</label>
        <select v-model.trip="tipo" class= "form-select" required>
          <option disabled select value=""> Selecciona un tipo de actividad </option>
          <option value="1"> Aplicaciones web con Vue.js</option>
          <option value="2"> Backed Services con Node.js</option>
          <option value="3"> App movil con React Native</option>
        </select>
      </div>

      <div class="mb-3 ">
         <input v-model="urgente" type="checkbox" class="form-check-input"/>
        <label class="form-check-label" for="exampleInputPassword1">Urgente</label>
      </div>

      <button type="submit" class="btn btn-primary">Guardar</button>
    </form>
    <hr>
    <div class="table-responsive">
      <table class="table table-dark table-hover">
        <thead>
          <tr>
            <th>#</th>
            <th>Proyecto</th>
            <th>Tipo</th>
            <th>Urgente</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(proyecto, index) in proyectos" :key="index">
            <td>{{index +1}}</td>
            <td>{{proyecto.proyecto}}</td>
            <td>{{proyecto.tipo}}</td>
            <td class="proyecto.urgente ? 'bg-sucess' : 'bg-danger' ">{{proyecto.urgente ? "si" : "no"}}</td>
          </tr>
        </tbody>
      </table>

    </div>
    <!--pre> <Codigo javascript sin marcar error>
      {{proyecto}}
      {{tipo}}
      {{urgente}}
    <pre-->
</template>