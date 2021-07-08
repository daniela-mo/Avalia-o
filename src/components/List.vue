<template>
  <div class="list">
    <div class="list__top">
      <h2>Lista de alunos</h2>

      <button @click="modal = true">Novo</button>
    </div>
    <table class="list__table">
      <thead>
        <tr>
          <th aria-checked=""></th>
          <th>Nome</th>
          <th>Email</th>
          <th>Skills</th>
          <th>Adicionado em:</th>
        </tr>
      </thead>
      <tbody v-for="aluno in alunos" :key="aluno.id">
        <td>{{ aluno.nome }}</td>
        <td>{{ aluno.email }}</td>
        <td>{{ aluno.skills }}</td>
        <td>{{ aluno.foto }}</td>
      </tbody>
    </table>

    <Modal v-if="modal">
      <div class="modal">
        <div>
          <h3 class="modal__title">Cadastrar novo aluno</h3>
        </div>
        <div class="modal__foto"></div>
        <form class="modal__form" action="">
          <input
            type="text"
            class="modal__form__input"
            placeholder="Nome"
            v-model="nome"
          />
          <input
            type="email"
            class="modal__form__input"
            placeholder="Email"
            v-model="email"
          />
          <input
            type="text"
            class="modal__form__input"
            placeholder="Digite as skills separadas por ','"
            v-model="skills"
          />
          <input
            type="text"
            class="modal__form__input"
            placeholder="Digite a url da foto"
            v-model="foto"
          />

          <button class="modal__form__btn" @click="adicionarAluno">
            Novo
          </button>
        </form>
      </div>
    </Modal>
  </div>
</template>

<style lang="scss" scoped>
.list {
  margin: 96px 38px;
  &__top {
    display: flex;
    justify-content: space-between;
    h2 {
      font-family: "Poppins", sans-serif;
      font-style: normal;
      font-weight: 500;
      font-size: 20px;
      line-height: 30px;
      text-align: right;
      letter-spacing: 0.01em;
      color: #109cf1;
    }
    button {
      border-radius: 5px;
      width: 160px;
      height: 42px;
      background: #109cf1;
      color: #fff;
      border: none;
      font-style: normal;
      font-weight: 600;
      font-size: 13px;
      line-height: 19px;
      text-align: center;
    }
  }
  &__table {
    width: 100%;
    justify-content: flex-start;
    margin-top: 26px;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
    background: #fff;
    thead {
      tr {
        th {
          font-family: "Poppins", sans-serif;
          font-size: 13px;
          height: 48px;
          color: #334d6e;
          opacity: 0.5;
        }
      }
    }
    tbody {
      td {
        height: 64px;
        border-top: #ebeff2;
        border-bottom: #ebeff2;
      }
    }
  }
}
.modal {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  padding: 20px;

  &__title {
    padding: 10px;
    border-bottom: 1px solid #c7c5c5;
  }
  &__foto {
    display: flex;
    margin-top: 10px;
    width: 138px;
    height: 138px;
    border-radius: 50%;
    background: #c4c4c4;
  }
  &__form {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    &__input {
      padding: 10px;
      width: calc(50%-5);
      height: 56px;
      margin: 10px 0;
      border: 1px solid rgba(25, 25, 25, 0.15);
      &:nth-child(1) {
        margin-right: 5px;
      }
      &:nth-child(3) {
        margin-right: 5px;
      }
    }
    &__btn {
      background: #109cf1;
      color: #fff;
      width: 160px;
      height: 42px;
      border-radius: 4px;
    }
  }
}
</style>

<script>
import axios from "axios";
import Modal from "@/components/Modal";
export default {
  data() {
    return {
      nome: "",
      email: "",
      skills: "",
      foto: "",
      modal: false,
      alunos: [],
    };
  },

  components: {
    Modal,
  },
  mounted() {
    this.listarAlunos();
  },
  methods: {
    async adicionarAluno(e) {
      const { data } = await axios.post("http://localhost:3000/alunos", {
        nome: this.nome,
        email: this.email,
        ra: this.ra,
        turma: this.turma,
      });
      this.modal = false;

      this.listarAlunos(
        (this.nome = ""),
        (this.email = ""),
        (this.skills = ""),
        (this.foto = "")
      );
    },
    async listarAlunos() {
      const { data } = await axios.get("http://localhost:3000/alunos");
      this.alunos = data;
    },
  },
};
</script>
