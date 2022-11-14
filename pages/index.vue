<template>
  <v-app>
    <v-app-bar app color="white" height="100">
      <v-avatar class="mr-3" color="grey lighten-5" size="70">
        <v-img contain max-height="70%" src="/images/logo.png"></v-img>
      </v-avatar>

      <v-toolbar-title class="font-weight-black headline">
        Vedum Minishop AS
      </v-toolbar-title>
    </v-app-bar>
    <v-content>
      <section id="hero">
        <div class="nedlagt-style">
        <p>
          Firmaet Vedum Minishop AS er nedlagt og ved forespørsel om varer eller eventuelt reklamasjon kan man ta kontakt på linken under.
        </p>
        <p>
          Anysharp knivslipere kontakt <a href="https://www.manao.no/">https://www.manao.no/</a> Mail: <a href="mailto:post@manao.no">post@manao.no</a>
        </p>
        <p>
          RP DEMO grensakser/sager kontakt <a href="www.rpdemoprodukter.se">www.rpdemoprodukter.se</a> Mail: <a href="mailto:info@rpdemo.se">mailto:info@rpdemo.se</a>
        </p>
        </div>
      </section>
    </v-content>

    <v-footer class="justify-center" color="#292929" height="100">
      <div
        class="title font-weight-light grey--text text--lighten-1 text-center"
      >
        &copy; {{ new Date().getFullYear() }} — Laget med 💜 av
        <a href="https://twitter.com/robaxelsen" class="skaper-link"
        >Robert Axelsen</a
        >
      </div>
    </v-footer>
  </v-app>
</template>

<script>
  import { products } from '../assets/data/products'

  export default {
    data() {
      return {
        valid: true,
        navn: "",
        epost: "",
        telefon: "",
        emne: "",
        mottaker: "",
        adresse: "",
        melding: "",
        produkter: [],
        stats: [
          ["10+", "Produkter"],
          ["60+", "Messer"],
          ["12000+", "Produkter solgt"]
        ]
      };
    },
    created() {
      this.produkter = products;
    },
    mounted() {
      document.title = "Vedum Minishop AS";
    },
    methods: {
      orderToday(reference) {
        this.melding = `${this.melding}Jeg ønsker å bestille ${reference}. `;
        this.$vuetify.goTo('#contact');
      },
      backToProducts() {
        this.$vuetify.goTo('#products');
      }
    }
  };
</script>

<style>
  .push-down {
    margin-top: 300px;
  }

  .stats {
    background: rgba(0, 0, 0, 0.75);
    border-radius: 5px;
  }

  .skaper-link,
  .skaper-link:active,
  .skaper-link:hover {
    color: #bdbdbd !important;
    text-decoration: none;
  }

  .nedlagt-style {
    padding: 30px;
  }
</style>
