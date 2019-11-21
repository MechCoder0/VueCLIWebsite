<template>
    <div>
        <div class="row">
            <div class="col-md-12">
                <div class="well">
                    <h2>Create a New Todo</h2>
                    <form>
                        <div class="form-group">
                            <label for="todoitem">Todo Item</label>
                            <input type="text" v-model="input" class="form-control" id="todoitem" placeholder="Todo Item" />
                        </div>
                        <button type="button" v-on:click="add()" class="btn btn-default">Create</button>
                    </form>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-md-12">
                <h2>List</h2>
                <h3>Total number of Todos: {{totalTodos}}</h3>
                <ul class="list-group">
                    <li v-for="(todo, index) in todos" :key="index" class="list-group-item">
                        {{ todo.id }}: {{ todo.data }}
                        <button type="button" v-on:click="remove(todo.id)" class="btn btn-default">Delete</button>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Todo",
    data () {
        return {
            todos: [],
            input: "",
            id: 0
        }
    },
    methods: {
        add() {
            var todo = {
                id: this.id,
                data: this.input
            }
            this.todos.push(todo);
            this.id ++;
            this.input = "";
        },
        remove (idToDelete) {
            this.todos = this.todos.filter(ele => ele.id !== idToDelete);
        }
    },
    computed: {
        totalTodos (){
            return this.todos.length;
        }
    }
}
</script>