<template>
  <div class="container mt-5">
    <Hello></Hello>
    <div class="row">
      <div class="col-8">
        <div class="card">
          <div class="card-header bg-dark text-light">
            Table
          </div>
          <div class="card-body">
            <table class="table">
              <thead class="">
                <tr>
                  <th>#</th>
                  <th>Name</th>
                  <th>Action</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(todo,index) in todos" :key="index">
                  <th scope="row">{{ index+1 }}</th>
                  <td>{{ todo }}</td>
                  <td>
                    <button @click.prevent="edit_todo(index,todo)" class="btn btn-info btn-sm mr-2">Edit</button>
                    <button  @click.prevent="delete_todo(index)" class="btn btn-danger btn-sm">Delete</button>
                  </td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
      <div class="col-4">
        <div class="card">
          <div class="card-header bg-dark text-light">
            Form
          </div>
          <div class="card-body">
            <div v-if="!isEditing">
              <form @submit.prevent="add_todo">
                <div class="form-group">
                  <label>Name</label>
                  <input v-model="name" type="text" class="form-control" placeholder="Enter Name">
                </div>
                <div class="form-group">
                  <button class="btn btn-primary" type="submit">Add</button>
                </div>
              </form>
            </div>
            <div v-else>
              <form @submit.prevent="update_todo">
                <div class="form-group">
                  <label>Name</label>
                  <input v-model="name" type="text" class="form-control" placeholder="Enter Name">
                </div>
                <div class="form-group">
                  <button class="btn btn-primary" type="submit">Update</button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      todos:['First','Second'],
      name:'',
      index:'',
      isEditing:false,
    }
  },
  methods: {
    add_todo(){
      this.todos.push(this.name)
      this.name = ""
    },

    edit_todo(id,todo){
       this.name = todo 
       this.index = id 
       this.isEditing = true
    },

    update_todo(){
      this.todos.splice(this.index,1,this.name)
      this.isEditing = false
      this.name = ""
    },

    delete_todo(id){
       this.todos.splice(id,1)
    }
  },
}
</script>

