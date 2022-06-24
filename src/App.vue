<template>
  <div id="app">
    <div class="col-md-6 mx-auto">
      <div class="card p-2">
        <div class="card-title">
          <h6>Ingresar Tareas</h6>
        </div>
        <div class="card-body">

          <div class="input-group">
            <input type="text" v-model="tarea"
                   class="form-control form-control-lg"
                   placeholder="Agregar tarea" autofocus>
            <div class="input-group-append">
              <button @click="addTarea()"
                      class="btn btn-success btn-lg">
                Agregar
              </button>
            </div>
          </div>

        </div>
      </div>
    </div>

    <Tareas msg="Lista de TAREAS"
            :listaTareas='listaTareas'
            @remove="removeTareaEnviada"/>

  </div>
</template>

<script>
  import Tareas from './components/Tareas.vue'

  export default {
    name: 'App',
    components: {
      Tareas
    },
    data() {
      return {
        tarea: '',
        listaTareas: [],
      }
    },
    methods: {
      addTarea() {
        const tarea = this.tarea
        if (tarea !== '') {
          this.listaTareas.push(tarea)
        }
        console.log(this.listaTareas)
        this.tarea = ''
      },
      removeTareaEnviada(t) {
        console.log(t)
        console.log(t.item)
        for (let i in this.listaTareas) {
          if (this.listaTareas[i] === t.item) {
            var n = parseInt(i)
          }
        }
        this.listaTareas.splice(n,1)
      }
    },
  }
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
