<script setup>
    const props = defineProps(['tarefas']);
</script>

    <template>
        <ul class="list-group mt-4">
            <li class="list-group-item" v-for="tarefa in props.tarefas">
                <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                    :id="tarefa.titulo" type="checkbox">
                <label :class="{ done: tarefa.finalizada === true }" class="ms-3" :for="tarefa.titulo">
                    {{ tarefa.titulo }}
                </label>
            </li>

            <br />

            <li class="list-group-item" v-if="props.tarefas.filter(t => !t.finalizada).length === 0">
                Não existem tarefas pendentes
            </li>
        </ul>
    </template>

<style scoped>
    .done {
        text-decoration: line-through;
    }
</style>