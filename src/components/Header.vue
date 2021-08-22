<template>
    <header class="header">
        <h1>Lista de tarefas do {{ nome }}</h1>
        <div class="button-input">
            <p>Para alterar o nome clique neste botão aqui --></p>
            <button @click="showInput">Abrir</button>
        </div>
        <div class="row">
            <input class="input-nome" type="text" v-model="nome" v-if="inputOnOff">
        </div>
    </header>
</template>

<script>
export default {
    data() {
        return {
            nome: '{nome}',
            inputOnOff: false,
        }
    },
    methods: {
        showInput() {
            if (this.inputOnOff == true) {
                this.inputOnOff = false;
            } else {
                this.inputOnOff = true;
            }
        }
    }
}
</script>

<style>
    .row {
        text-align: center;
        margin-top: 15px;
    }
    .row .input-nome {
        width: 300px;
        border: none;
        outline: none;
        padding: 3px 15px;
        border-radius: 5px;
    }
    .button-input {
        gap: 15px;
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .button-input p {
        color: rgb(199, 199, 199);
    }
    .button-input button {
        border-radius: 2px;
        cursor: pointer;
        border: 1px solid white;
        padding: 2px 20px;
        background: transparent;
        color: white;
        display: inline-block;
    }
    .header {
        background: linear-gradient(135deg, #233f61, #335681);
        padding: 30px;
    }
    .header h1 {
        color: #fff;
        text-align: center;
    }
</style>