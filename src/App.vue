<template>
  <nav class="navbar navbar-dark bg-primary">
    <div class="container-fluid">
      <a
        class="navbar-brand"
        href="#"
        style="font-family: 'Quicksand', sans-serif"
      >
        <img
          src="https://img.icons8.com/cotton/2x/image--v2.png"
          alt="none"
          width="28"
          height="30"
          class="d-inline-block align-text-top"
        />
        Pise Company
      </a>
    </div>
  </nav>

  <!-- lista delle cose da fare -->
  <ul id="lista" class="list-group tab-pane fade show active">
    <li class="list-group-item" v-for="(todo, index) in list" :key="index">
      <input
        class="form-check-input me-1"
        type="checkbox"
        v-model="todo.completed"
      />
      {{ todo.title }}
    </li>
  </ul>

  <div
    class="modal fade"
    id="exampleModal"
    tabindex="-1"
    aria-labelledby="exampleModalLabel"
    aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Inserimento</h5>
          <button
            type="button"
            class="btn-close"
            data-bs-dismiss="modal"
            aria-label="Close"
          ></button>
        </div>

        <!-- comando per aggiungere nuova attività -->
        <div class="modal-body">
          Inserisci nuova To-Do list

          <br /><br />

          <!-- aggiungiamo l'input -->
          <div class="input-group input-group-sm mb-3">
            <input
              id="add"
              type="text"
              v-model="newTitle"
              class="form-control"
              aria-label="Sizing example input"
              aria-describedby="inputGroup-sizing-sm"
            />
          </div>
        </div>
        <div class="modal-footer">
          <button
            type="button"
            class="btn btn-secondary"
            data-bs-dismiss="modal"
          >
            Close
          </button>
          <button @click="aggiungi()" type="button" class="btn btn-primary">
            Conferma
          </button>
        </div>
      </div>
    </div>
  </div>

  <div id="infondo" class="d-grid gap-2">
    <button
      class="btn btn-primary"
      type="button"
      data-bs-toggle="modal"
      data-bs-target="#exampleModal"
    >
      Aggiungi un to-do
    </button>
    <button @click="elimina()" class="btn btn-danger" type="button">
      Elimina i to-do
    </button>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      newTitle: "",
      list: [
        {
          title: "Fare la spesa",
          completed: false,
        },
        {
          title: "Comprare il motorino",
          completed: false,
        },
        {
          title: "Comprare la RTX 3080",
          completed: false,
        },
        {
          title: "Andare a messa",
          completed: true,
        },
        {
          title: "Andare a cena",
          completed: false,
        },
      ],
    };
  },
  methods: {
    aggiungi() {
      this.list.push({
        title: this.newTitle,
        completed: false,
      });
      this.newTitle = "";
    },
    elimina(){
      let i = this.list.length;
      while (i--) {
        if (this.list[i].completed) {
          this.list.splice(i, 1);
        }
      }
    },
  },
};
</script>

<style>
#infondo {
  position: fixed;
  bottom: 0px;
  width: 100%;
}
</style>
