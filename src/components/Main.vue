<template>
    <main class="main">
        <section class="main__inputTask">
            <article class="main__inputTask__input-button">
                <input @keyup.enter="addTask" v-model="newTask" type="text">
                <a @click="addTask" href="#"><span>Adicionar tarefa</span><i class="fas fa-check"></i></a>
            </article>
        </section>
        <section v-if="tarefas.length > 0" class="tasks">
            <article class="tasks__article">
                <ul class="taskList">
                    <li :class="{ feito: task.checked }" v-for="(task, index) in tarefas" @click="$emit('chamadoIndex', index)" :key="index">
                        <div class="checkbox">
                            <i v-if="task.checked" class="fas fa-check-square" style="color: green;"></i>
                            <i v-else class="far fa-check-square"></i>
                        </div>
                        <span :class="{ riscado: task.checked }">{{ task.nome }}</span>
                        <span class="texto-feito" v-if="task.checked">FEITO!</span>
                    </li>
                </ul>
            </article>
        </section>
    </main>
</template>

<script>
export default {
    props: ['tarefas'],
    data() {
        return {
            newTask: '',
        }
    },
    methods: {
        addTask() {
            if (this.newTask == '') {
                window.alert('Você não pode adicionar tarefas com nomes vazios')
            } else {
                this.$emit('chamadoAddTask', this.newTask)
                this.newTask = '';
            }
            
        },
    },
}
</script>

<style>
    .texto-feito {
        font-size: 0.9em;
        top: 50%;
        transform: translateY(-50%);
        right: 20px;
        position: absolute;
    }
    .feito {
        background: rgb(161, 231, 161);

    }
    .riscado {
        color: rgba(100, 100, 100, 0.274);
        text-decoration: line-through;
    }
    .taskList li {
        position: relative;
        border-radius: 3px;
        padding: 10px 30px;
        cursor: pointer;
        display: flex;
    }
    .taskList li + li {
        margin-top: 5px;
    }
    .taskList li span:first-child {
        margin-left: 5px;
        height: 100%;
        flex: 1;
        text-align: left;
    }
    .checkbox {
        text-align: center;
        width: 30px;
        height: 100%;
    }
    .tasks {
        padding: 30px 0;
    }
    .tasks__article {
        border-radius: 10px;
        padding: 40px;
        box-shadow: 5px 5px 15px gray;
        width: 400px;
        margin: 0 auto;
    }
    .main__inputTask {
        box-shadow: 0 4px 15px -2px gray;
        padding: 30px 0;
    }
    .main__inputTask__input-button {
        align-items: center;
        gap: 10px;
        display: flex;
        width: 850px;
        margin: 0 auto;
    }
    .main .main__inputTask input {
        font-size: 15px;
        outline: none;
        border: 1px solid black;
        border-radius: 3px;
        flex: 1;
        padding: 5px 20px;
    }
    .main .main__inputTask a {
        border-radius: 3px;
        background: #335681;
        position: relative;
        padding: 5px 30px;
    }
    .main .main__inputTask a i {
        font-size: 1.1em;
        margin-left: 8px;
    }
    .main .main__inputTask a i, .main .main__inputTask a span {
        font-size: 0.95rem;
        color: white;
    }
</style>