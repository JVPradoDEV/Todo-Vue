<script setup>
const props = defineProps(['tarefas']);

function semPendentes(){
    if (props.tarefas.length === 0){
        return true
    } else {
        return false
    }

}
</script>


<template>
    <ul v-if="semPendentes() === false" class="list group mt-4">
        <li class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ done: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
    </ul>
    <ul class="list group mt-4" v-else="semPendentes() === true">
        <li class="list-group-item">
            <h3>Sem tarefas por aqui! 🎉</h3>
        </li>
    </ul>
</template>

<style scoped>
.done {
    text-decoration: line-through;
}
</style>