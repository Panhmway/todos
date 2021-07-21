<template>
  <div id="app" class="container">
  <notifications group="foo" />
   <div class="row justify-content-center">
     <legend class="text-center text-white my-4">{{name}}'sToDo List</legend>
     <input type="text" class="form-control col-5" v-model="task" @keyup.enter="addItem()">
     <button class="btn bg-dark text-white ml-3" @click="addItem()">Add Item</button>

    
      <div class="col-7 mt-3">  
        <transition-group
          enter-active-class="animate__animated animate__slideInDown"
          leave-active-class="animate__animated animate__backOutDown"
        >
         <div class="card mb-2" v-for="(todo,index) in toDos" :key="index">
           <div class="row p-3 align-items-center mt-2">
             <div class="col-7 mt-2 ml-2" :class="{cross : todo.done == true}">
                <h5>{{todo.item}}</h5>
             </div>
             <div class="col text-center">
               <button class="btn btn-sm btn-success mr-3 pt-2" @click="done(index)">
                 <i class="material-icons ">check</i>
               </button>
               <button class="btn btn-sm btn-danger pt-2" @click="deleteTask(index)">
                 <i class="material-icons ">delete</i>
               </button>
             </div>
           </div>
         </div>
         </transition-group>
       </div>
   
   </div>
  </div>
</template>

<script>
export default {
 name :'App',
 data(){
   return{
     name:'PanHmway',
     task:'',
     toDos:[]
   }
 },

 methods : {
   addItem(){
     if(this.task !=''){
      //  this.toDos.push(this.task)
      this.toDos.push({
        done:false,
        item:this.task
      })
      this.task=''

      this.$notify({
        group: 'foo',
        title: 'Important message',
        text: 'Hello user! This is a notification!'
      });

     }else{
       alert('Please write ToDo task!')
     }
   },
   deleteTask(index){
     if(confirm('are you sure to Delete')){
       this.toDos.splice(index,1)

      this.$notify({
        group: 'foo',
        title: 'Deleted!',
        text: 'Hello user! This is a notification!',
        type:'error',
      });

     }
   },
   done(index){
     this.toDos[index].done = true
    this.$notify({
      group: 'foo',
      title: 'Checked!',
      text: 'Hello user! This is a notification!',
      type:'warn',
    });
   }
 }
}
</script>

<style>
.card{
  border-radius: 10px !important;
}
.cross{
  text-decoration: line-through;
}
</style>