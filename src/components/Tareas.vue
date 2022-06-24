<template>
  <div class="tareas mt-3 px-5">
    <div class="text-center col-10 col-md-8 mx-auto">
      <h6>{{ msg }}</h6>

      <table class="table table-striped table-responsive">
        <thead>
          <tr>
            <th>#</th>
            <th>Tarea</th>
            <th><i class="fas fa-trash"></i></th>
          </tr>
        </thead>
        <tbody>
        <tr v-for="(item, index) in listaTareas" :key="index">
          <td>{{index +1 }}</td>
          <td>{{item}}</td>
          <td>
            <button @click="removeTarea({item})"
                class="btn btn-outline-danger btn-sm" type="submit">
              <i class="fas fa-trash"></i>
            </button>
          </td>
        </tr>
        </tbody>
      </table>

    </div>
  </div>
</template>

<script>
  export default {
    name: 'Tareas',
    props: {
      msg: String,
      listaTareas: Array,
    },
    data() {
      return {
      }
    },
    methods:{
      removeTarea(item){
        // console.log(item)
        this.$emit('remove', item)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

</style>
