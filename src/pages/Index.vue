<template>
  <q-page class="flex flex-center" style="min-height: 200px">
    <div class="block">
      <input type="text" v-model="search" id="searchInput" class="input-res" />

      <label for="searchInput">Pesquise aqui pelo nome do cliente</label>
    </div>
    <table id="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Nome</th>
          <th scope="col">CPF</th>
          <th scope="col">Fidelidade</th>
          <th scope="col">Controlar fidelidade</th>
        </tr>
      </thead>

      <tbody>
        <tr v-for="(item, i) in filteredItems" :key="i">
          <td data-label="#">&nbsp; {{ item.rank }}</td>
          <td data-label="Nome:">&nbsp;{{ item.nome }}</td>
          <td data-label="CPF:">&nbsp;{{ item.cpf }}</td>
          <td data-label="Fidelidade:">&nbsp;{{ item.fidelidade }} &nbsp;
<q-banner inline-actions class="text-white bg-green" v-if="item.fidelidade >= 10">
    {{item.nome}} atingiu {{item.fidelidade}} pontos de fidelidade!!!

    </q-banner>

          </td>
          <td><button @click="fidem1(i)">+1</button><button @click="fidemen1(i)">-1</button></td>
        </tr>
      </tbody>
    </table>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "PageIndex",

  data() {
    return {
      search: "",
      items: [

        {
          rank: "1",
          nome: "luiz eduardo",
          cpf: "07898148380",
          fidelidade: 0,
        },
         {
          rank: "2",
          nome: "lucas",
          cpf: "04789851235",
          fidelidade: 0,
        },
         {
          rank: "3",
          nome: "Adri",
          cpf: "78412687984",
          fidelidade: 0,
        },
      ],
    };
  },

 mounted() {
    if (localStorage.getItem('items')) {
      try {
        this.items = JSON.parse(localStorage.getItem('items'));
      } catch(e) {
        localStorage.removeItem('items');
      }
    }
  },
  computed: {
    filteredItems() {
      return this.items.filter((item) => {
        return item.nome.toLowerCase().indexOf(this.search.toLowerCase()) > -1;
      });
    },
  },
  methods: {
    fidem1(i) {
      this.items[i].fidelidade++
      localStorage.items = JSON.stringify(this.items)
    },
     fidemen1(i) {
    if( this.items[i].fidelidade >= 1) {
        this.items[i].fidelidade--
        localStorage.items = JSON.stringify(this.items)
    }
    },
  },
});
</script>

<style>
table {
  border: 1px solid #ccc;
  border-collapse: collapse;
  margin: 0;
  padding: 0;
  width: 100%;
  table-layout: fixed;
}

table caption {
  font-size: 1.5em;
  margin: 0.5em 0 0.75em;
}

table tr {
  background-color: #f8f8f8;
  border: 1px solid #ddd;
  padding: 0.35em;
}

table th,
table td {
  padding: 0.625em;
  text-align: center;
}

table th {
  font-size: 0.85em;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

@media screen and (max-width: 600px) {
  table {
    border: 0;
  }

  table caption {
    font-size: 1.3em;
  }

  table thead {
    border: none;
    clip: rect(0 0 0 0);
    height: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
    width: 1px;
  }

  table tr {
    border-bottom: 3px solid #ddd;
    display: block;
    margin-bottom: 0.625em;
  }

  table td {
    border-bottom: 1px solid #ddd;
    display: block;
    font-size: 15px;
    text-align: right;
  }

  table td::before {
    /*
    * aria-label has no advantage, it won't be read inside a table
    content: attr(aria-label);
    */
    content: attr(data-label);
    float: left;
    font-weight: bold;
    text-transform: uppercase;
  }

  table td:last-child {
    border-bottom: 0;
  }
}

.block {
  margin: 0 auto;
  max-width: 900px;
  padding: 50px 30px;
}
.input-res {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  font: 15px/1 "Open Sans", sans-serif;
  color: white;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100%;
  max-width: 500px;
  background-color: #455a64;
  border: none;
  padding: 10px 11px 11px 11px;
  border-radius: 3px;
  box-shadow: none;
  outline: none;
  margin: 0;
  box-sizing: border-box;
}
</style>
