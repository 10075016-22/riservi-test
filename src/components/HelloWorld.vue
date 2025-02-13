<template>
  <html>
    <head> </head>

    <body>
      <div id="contenedor">
        <div class="bloque1">
          <p>Este es el Bloque 1 dentro del contenedor.</p>
        </div>

        <div class="bloque2">
          <p>
            Este es el contenido del Bloque 2 dentro del contenedor, este
            contiene mas texto, por eso debe ser mas largo.
          </p>
        </div>
        <div class="clear"></div>
      </div>

      <div class="bloque1">
        <p>Este es el Bloque 1 fuera del contenedor.</p>
      </div>

      <div class="bloque2">
        <p>Este es el Bloque 2 fuera del contenedor.</p>
      </div>

      <div class="v-container">
        <div v-for="(item, index) in cmpArray" :key="index" :class="[index % 2 !== 0 ? 'bg-grey' : '']">
          {{ item.name }}, {{ item.rolesJoin}}
        </div>
      </div>
      <div class="btn" @click="onGenerar">Generar</div>
      <div class="output">
        {{ output }}
      </div>
    </body>
  </html>
</template>
<script>
export default {
  name: "SupportView",
  components: {},
  data() {
    return {
      myArray: [],
      output: "",
    };
  },
  mounted() {
    setTimeout(() => this.onLlenarArray(), 500);
  },
  computed: {
    cmpArray() {
      return this.myArray.map((oItem) => {
        return {
          name: oItem.name,
          rolesJoin: oItem.roles?.join(',')
        }
      })
    }
  },
  methods: {
    onLlenarArray() {
      this.myArray = [
        {
          id: 1,
          name: "Test 1",
          roles: [1, 2, 3, 4, 5, 6, 7],
        },
        {
          id: 2,
          name: "Test 2",
          roles: [2, 3, 7],
        },
        {
          id: 3,
          name: "Test 3",
          roles: [1, 2, 4],
        },
        {
          id: 4,
          name: "Test 4",
          roles: [1, 2, 7],
        },
        {
          id: 5,
          name: "Test 5",
          roles: [1, 6, 7],
        },
      ];
    },
    onGenerar() {
      this.output = `El total de listado es: ${this.cmpArray.length}`
    }
  },
};
</script>

<style>
.btn:hover {
  cursor: pointer;
}
.clear {
  clear: both;
}
body {
  text-align: center;
}

p {
  padding: 10px;
}

#contenedor {
  width: 600px;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px dotted grey;
  margin: auto;
}

#contenedor .bloque1 {
  width: 100px;
  margin-top: 70px !important;
}
#contenedor .bloque2 {
  width: 100px;
}

#contenedor .bloque1, #contenedor .bloque2 {
  float: left;
  margin: 5px;
}

/* italica para parrafo bloque 1 */
#contenedor > .bloque1 p {
  font-style: italic;
}

.bloque1 {
  background: red;
  color: #ffffff;
}
.bloque2 {
  background-color: yellow;
  color: #000000;
}
.bloque2 p {
  font-weight: bold;
}

.bg-grey {
  background-color: #E6E6E6;

}
</style>