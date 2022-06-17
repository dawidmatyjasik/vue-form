<template>
  <div class="container">
    <div class="form">
      <h1>Rekrutacja</h1>
      <form>
        <div>
          <label for="name">Imię</label>
          <input type="text" id="name" v-model="formValues.name" />
        </div>
        <div>
          <label for="surname">Nazwisko</label>
          <input type="text" id="surname" v-model="formValues.surname" />
        </div>
        <div>
          <label for="country">Kraj</label>
          <select id="country" v-model="formValues.country">
            <option value="">Wybierz kraj</option>
            <option value="india">Polska</option>
            <option value="vietnam">Niemcy</option>
            <option value="singapore">Rosja</option>
          </select>
        </div>
        <div>
          <label>Umiejętności</label>
          <input
            type="checkbox"
            id="html"
            value="html"
            v-model="formValues.skillSet"
          />
          <label for="html">HTML</label>
          <input
            type="checkbox"
            id="css"
            value="css"
            v-model="formValues.skillSet"
          />
          <label for="css">CSS</label>
          <input
            type="checkbox"
            id="javascript"
            value="javascript"
            v-model="formValues.skillSet"
          />
          <label for="javascript">JavaScript</label>
        </div>
        <div>
          <input id="rodo" type="checkbox" v-model="formValues.rodo" />
          <label for="rodo"
            >Zapoznałem się z regulaminem przetwarzania danych RODO</label
          >
        </div>
        <button @click.prevent="submitForm">Aplikuj</button>
      </form>
    </div>
    <iframe
      width="420"
      height="345"
      src="https://www.youtube.com/embed/tgbNymZ7vqY"
    >
    </iframe>
  </div>
</template>

<script>
import useValidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";
export default {
  name: "App",
  components: {},
  data() {
    return {
      v$: useValidate(),
      formValues: {
        name: "",
        surname: "",
        country: "",
        skillSet: [],
        rodo: "",
      },
    };
  },

  validations() {
    return {
      formValues: {
        name: { required },
        surname: { required },
        country: { required },
        skillSet: { required },
        rodo: { required },
      },
    };
  },

  methods: {
    submitForm() {
      this.v$.$validate();
      if (!this.v$.$error) {
        alert("Zgłoszenie zostało przesłane!");
      } else {
        alert("Sprawdź czy wszystkie wartości są uzupełnione!");
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
div {
  margin-bottom: 10px;
}
label {
  font-weight: bold;
  display: flex;
  margin-bottom: 5px;
}
input + label {
  font-weight: bold;
  display: inline-flex;
  margin-right: 20px;
}
input[type="text"],
textarea,
select {
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 4px;
}
iframe {
  margin-top: 20px;
}
.container {
  display: flex;
  justify-content: space-evenly;
}
button {
  padding: 8px 20px;
  background: white;
  border: 1px solid #555;
  border-radius: 5px;
}
</style>
