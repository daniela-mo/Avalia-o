<template>
  <div class="list">
    <div class="list__content">
      <div class="list__content__title">
        <h2>Lista de alunos</h2>
        <button @click="modal = true">Novo</button>
      </div>

      <table class="list__content__table">
        <thead class="list__content__table__thead">
          <tr>
            <input type="checkbox" />
            <th>Nome</th>
            <th>Email</th>
            <th>Skills</th>
            <th>Adicionado em:</th>
          </tr>
        </thead>
        <tbody
          class="list__content__table__tbody"
          v-for="aluno in alunos"
          :key="aluno.id"
        >
          <tr>
            <input type="checkbox" />
            <td>{{ aluno.nome }}</td>
            <td>{{ aluno.email }}</td>
            <td>
              <div class="list__content__table__tbody__html">HTML</div>
              <div class="list__content__table__tbody__vue">VUE</div>
              <div class="list__content__table__tbody__react">REACTE</div>
              <div class="list__content__table__tbody__angular">ANGULAR</div>
            </td>
            <td>5 Minutes ago</td>
          </tr>
        </tbody>
      </table>
    </div>
    <Modal v-if="modal">
      <div class="modal">
        <div class="modal__title">
          <h3>Cadastro novo aluno</h3>
        </div>
        <div class="modal__foto"></div>
        <div>
          <form class="modal__form">
            <input
              type="text"
              placeholder="Nome"
              v-model="nome"
              class="modal__form__nome"
            />
            <input
              type="text"
              placeholder="Email"
              v-model="email"
              class="modal__form__email"
            />
            <input
              type="text"
              class="modal__form__skills"
              v-model="skills"
              placeholder="Digite as skills separadas por ','"
            />
            <input
              type="text"
              class="modal__form__foto"
              placeholder="Digite a url da foto"
            />
            <div class="modal__form__btn">
              <button @click="adicionarAluno">
                Novo
              </button>
            </div>
          </form>
        </div>
      </div>
    </Modal>
  </div>
</template>

<style lang="scss" scoped>
.list {
  display: flex;
  width: 100%;
  height: 100%;
  &__content {
    width: 1800px;
    margin: 26px 38px;
    &__title {
      width: 1800px;
      margin: 26px 38px;
      display: flex;
      justify-content: space-between;
      h2 {
        color: #109cf1;
        font-style: normal;
        font-family: Poppins;
        font-style: normal;
        font-weight: 500;
      }
      button {
        background: #109cf1;
        width: 160px;
        height: 42px;
        border-radius: 4px;
        border: none;
        color: #fff;
      }
    }
    &__table {
      margin: 0 38px;
      background: #fff;
      &__thead {
        width: 1800px;
        display: flex;
        tr {
          padding: 20px 0;
          display: flex;
          input {
            width: 16px;
            height: 16px;
            border-radius: 4px;
            margin: 0 10px;
          }
          th {
            display: flex;
            width: 500px;
            color: #98a5b6;
            font-style: normal;
            font-weight: 500;
            font-size: 13px;
          }
        }
      }
      &__tbody {
        width: 1800px;
        display: flex;

        tr {
          padding: 20px 0;
          display: flex;
          input {
            width: 16px;
            height: 16px;
            border-radius: 4px;
            margin: 0 10px;
          }
          td {
            display: flex;
            width: 500px;
            font-style: normal;
            font-weight: normal;
            font-size: 13px;
            line-height: 19px;
            text-align: right;
          }
        }
        &__html {
          width: 50px;
          border: 1px solid #109cf1;
          margin-left: 10px;
          display: flex;
          align-items: center;
          justify-content: center;
          font-style: normal;
          color: #109cf1;
          font-weight: 500;
          font-size: 13px;
          line-height: 19px;
          height: 30px;
        }
        &__vue {
          width: 50px;
          border: 1px solid #109cf1;
          margin-left: 10px;
          display: flex;
          align-items: center;
          justify-content: center;
          color: #109cf1;
          font-style: normal;
          font-weight: 500;
          font-size: 13px;
          line-height: 19px;
          height: 30px;
        }
        &__react {
          width: 70px;
          border: 1px solid #109cf1;
          margin-left: 10px;
          display: flex;
          align-items: center;
          justify-content: center;
          color: #109cf1;
          font-style: normal;
          font-weight: 500;
          font-size: 13px;
          line-height: 19px;
          height: 30px;
        }
        &__angular {
          width: 80px;
          border: 1px solid #109cf1;
          margin-left: 10px;
          display: flex;
          align-items: center;
          justify-content: center;
          font-style: normal;
          font-weight: 500;
          font-size: 13px;
          line-height: 19px;
          color: #109cf1;
          height: 30px;
        }
      }
    }
  }
  .modal {
    display: flex;
    width: 100%;
    height: 100%;
    padding: 20px;
    flex-direction: column;
    &__title {
      padding: 10px;
      font-style: normal;
      font-weight: normal;
      font-size: 18px;
      border-bottom: 1px solid #c7c5c5;
    }
    &__foto {
      display: flex;
      align-items: center;
      margin: 10px 160px 0 160px;
      width: 138px;
      height: 138px;
      border-radius: 50%;
      background: #c4c4c4;
    }
    &__form {
      &__nome {
        width: 240px;

        flex-wrap: wrap;
        height: 56px;
        margin-right: 15px;
        margin-top: 26px;
      }
      &__email {
        width: 240px;
        height: 56px;
        flex-wrap: wrap;
        margin-top: 26px;
      }

      &__skills {
        width: 496px;
        height: 56px;
        margin-top: 26px;
      }
      &__foto {
        width: 496px;
        display: flex;

        height: 56px;
        margin-top: 26px;
      }
      input {
        padding-left: 10px;
        outline: none;
        border: 1px solid rgba(25, 25, 25, 0.32);
      }
      &__btn {
        display: flex;
        justify-content: flex-end;
        button {
          width: 160px;
          height: 42px;
          border-radius: 4px;
          border: 1px solid #109cf1;
          color: #fff;
          font-size: 13px;
          font-weight: 600;
          font-style: normal;
          margin-top: 26px;
          background: #109cf1;
        }
      }
    }
  }
}
</style>

<script>
import axios from "axios";
import Modal from "@/components/Modal";
export default {
  components: {
    Modal,
  },
  data() {
    return {
      nome: "",
      email: "",

      modal: false,
      alunos: [],
    };
  },

  mounted() {
    this.listarAlunos();
  },
  methods: {
    async adicionarAluno(e) {
      const { data } = await axios.post(" http://localhost:3000/alunos", {
        nome: this.nome,
        email: this.email,
        skills: this.skills,
      });
      this.modal = false;

      this.listarAluno()((this.nome = "")), (this.nome = ""), (this.nome = "");
    },

    async listarAlunos() {
      const { data } = await axios.get("http://localhost:3000/alunos");
      this.alunos = data;
    },
  },
};
</script>
