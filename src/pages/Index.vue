<template>
  <!-- <q-page class="flex flex-center"> -->
  <q-page >
  	<q-input
        filled
        square
        bordered
        class="q-px-md q-pt-md"
        bg-color="white"
        bottom-slots
        v-model="newTask"
        placeholder="Add Task"
        maxlength="12"
        :dense="dense"
        @keyup.enter="tambahTask"
        >
        <template v-slot:append>
          <q-btn round dense flat icon="add" @click="tambahTask"/>
        </template>
      </q-input>
  	<q-list v-for="(todo,index) in todos" :key="todo.title">
	  	 <q-item
			  	 @click="todo.status = !todo.status"
			  	 clickable
			  	 v-ripple
			  	 :class="{'done bg-blue-1' : todo.status}"
			  	 >
	        <q-item-section side top>
	          <q-checkbox
		          v-model="todo.status"
		          class="no-pointer-events" />
	        </q-item-section>
	        <q-item-section >
	          <q-item-label>
	            {{todo.title}}
	          </q-item-label>
	        </q-item-section>
	        <q-item-section
	        	@click.stop="removeTodo(index)"
		        side
		        v-if="todo.status" >
	        	<q-btn
		        	flat
		        	round
		        	color="primary"
		        	icon="delete"/>
	        </q-item-section>
	      </q-item>
	      <q-separator />
      </q-list>

  </q-page>
</template>

<script>
export default {
  data(){
  	return{
  		newTask:'',
  		dense:false,
  		todos:[
        // {
        //   title:'Membeli Baju',
        //   status:false
        // },
        // {
        //   title:'Membeli Sepatu',
        //   status:false
        // },
        // {
        //   title:'Membeli Kue',
        //   status:false
        // }
      ],
  	}
  },
 methods:{
 	removeTodo(index){
 		this.todos.splice(index, 1)
 	},
 	tambahTask(){
 		this.todos.push({
 			title:this.newTask,
 			status:false,
 		})
 		this.newTask=''
 	},
 }
}
</script>

<style lang="scss">
	.done{
		.q-item__label{
			text-decoration: line-through;
			color:#bbb;
		}

	}
</style>
