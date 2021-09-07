<template>


    <div class="item">



        <input @change="updateToDo()" type="checkbox" v-model="item.completed">
        <span :class="['itemText', item.completed? 'completed' : '']">{{item.todo}}</span>
        <button class="edit btn btn-secondary">
            Edit
        </button>
        <button class="btn btn-danger" @click="removeToDo()">
            Delete
        </button>


    </div>

</template>

<script>
export default {
    props: ['item'],

    methods: {
        updateToDo(){
            axios.post('api/todos/update/' + this.item.id ,{
                completed: this.item.completed
            }).then(response=>{
                if(response.status >= 200 && response.status < 300){
                    alert("item updated successfully");
                    this.$emit('reloadToDos');
                }
            })
        },


        removeToDo(){
            //alert("triggered");
            axios.post('api/todos/delete/' + this.item.id).then(response=>{
                if(response.status >= 200 && response.status < 300){
                    alert("item deleted successfully");
                    this.$emit('reloadToDos');
                }
            })
        }

    },
}
</script>

<style scoped>

</style>
