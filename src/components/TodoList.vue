<template>
    <div>
        <ul>
            <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:['propsdata'],
    methods: {
        removeTodo(todoItem, index) {
            //localStorage.removeItem(todoItem);
            this.$emit('removeTodo', todoItem, index);
            this.todoItems.splice(index, 1);  //splice(index, cnt) : index에서 cnt만큼 삭제하는 자바스크립트 내장API

        },
    }
}
</script>

<style scoped>
    ul {
        list-style: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }

    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }

    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
</style>