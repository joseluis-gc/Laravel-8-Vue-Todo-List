<template>
   <div>
       <div class="container">
           <h1 class="text-center">Todo</h1>
            <div class="todolistcontainer">
                <add-item-form />
                <list-view />
            </div>
       </div>
   </div>
</template>

<script>
    import addItemForm from './addItemForm.vue';
    import listView from './listView.vue';


    export default {
        components: {
            addItemForm,
            listView
        }
    }
</script>
<style scoped>
    .todolistcontainer{
        width: 400px;
        margin: auto;
        margin-top: 50px;
    }
</style>
