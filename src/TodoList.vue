<template>
    <section id="Todo">
      <div class="container-fluid">
        <div class="row ">
          <div class="col-md-6 mx-auto">
            <h1 class="text-center">Todo List</h1>
            <div class="form-group ">
              <form action="#" v-on:submit.prevent="AddTodo()">
                <div class="input-group">
                  <input type="text" placeholder="Enter Job" class="form-control w-50 mx-auto " v-model="Todo">
                  <div class="input-group-append">
                    <button type="submit" class="btn btn-primary" >Submit</button>
                  </div>
                </div>
              </form>
            </div>
            <div class="mx-auto">
              <ul>
                <li v-for="item in Todos"  class="d-flex my-3 ">

                    <label class="form-check-label h3" :class="{ done : Todos.Done  }">{{item.Title}}</label>
                  <button type="button" class="btn btn-primary ml-4" v-on:click="RemoveTodo(item)">Remove</button>

                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>
</template>

<script>

    export default {
     data(){
         return{
             Todo:'',
             Todos:[]
         }
     },
        methods:{
            AddTodo(){
                this.Todos.push({Title:this.Todo,Done:false})
               this.Todo=''

            },
            RemoveTodo(Todo){

          const RemoveTodo=this.Todos.indexOf(Todo)
                this.Todos.splice(RemoveTodo,1)
            }
        }

    }
</script>

<style scoped>
.done{
  color: green;
}
</style>
