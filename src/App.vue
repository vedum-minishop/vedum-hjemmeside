<template>
  <v-app>
    <v-app-bar app color="white" height="100">
      <v-avatar class="mr-3" color="grey lighten-5" size="70">
        <v-img contain max-height="70%" src="/logo.png"></v-img>
      </v-avatar>

      <v-toolbar-title class="font-weight-black headline">
        Vedum Minishop AS
      </v-toolbar-title>
    </v-app-bar>
    <v-content>
      <section id="hero">
        <v-row no-gutters>
          <v-img
            :min-height="'calc(100vh - ' + $vuetify.application.top + 'px)'"
            src="/cover.png"
          >
            <v-theme-provider dark>
              <v-container fill-height>
                <v-row
                  align="center"
                  class="white--text mx-auto push-down"
                  justify="center"
                >
                  <v-btn
                    class="align-self-end"
                    fab
                    outlined
                    @click="$vuetify.goTo('#about-me')"
                  >
                    <v-icon>mdi-chevron-double-down</v-icon>
                  </v-btn>
                </v-row>
              </v-container>
            </v-theme-provider>
          </v-img>
        </v-row>
      </section>

      <section id="about-me">
        <div class="py-12"></div>

        <v-container class="text-center">
          <h2 class="display-2 font-weight-bold mb-3">OM OSS</h2>

          <v-responsive class="mx-auto mb-8" width="56">
            <v-divider class="mb-1"></v-divider>

            <v-divider></v-divider>
          </v-responsive>

          <v-responsive
            class="mx-auto title font-weight-light mb-8"
            max-width="720"
          >
            Vedum Minishop har eksistert i to generasjoner og har alltid satset
            på kvalitetsvarer. Vi har orginalvarer med høy kvalitet og det er
            helt vesentlig å kunne tilby dette til dere som kunder. Det kan
            nevnes knivslipere som Anysharp av stål og er helt suveren med 10
            års garanti. Vi kan fortsette med andre slipeprodukter og ender med
            elektriske knivslipere fra Chef`sChoice for de som har mere enn de
            fleste innen kniver. Det er bare å sende en forespørsel/ringe så vil
            vi anbefale. CoverBlubber er lokk som kan brukes på forskjellige
            matvarer eller lokk på skåler. Disse kan brukes direkte på matvarene
            og skylles lett av med såpe og vann. De er helt super.
          </v-responsive>
        </v-container>

        <div class="py-12"></div>
      </section>

      <section id="stats">
        <v-parallax
          :height="$vuetify.breakpoint.smAndDown ? 700 : 500"
          src="/messe.png"
        >
          <v-container fill-height>
            <v-row class="mx-auto stats">
              <v-col
                v-for="[value, title] of stats"
                :key="title"
                cols="12"
                md="3"
              >
                <div class="text-center">
                  <div
                    class="display-3 font-weight-black mb-4"
                    v-text="value"
                  ></div>

                  <div
                    class="title font-weight-regular text-uppercase"
                    v-text="title"
                  ></div>
                </div>
              </v-col>
            </v-row>
          </v-container>
        </v-parallax>
      </section>

      <section id="blog">
        <div class="py-12"></div>

        <v-container>
          <h2
            class="display-2 font-weight-bold mb-3 text-uppercase text-center"
          >
            Produkter
          </h2>

          <v-responsive class="mx-auto mb-12" width="56">
            <v-divider class="mb-1"></v-divider>

            <v-divider></v-divider>
          </v-responsive>

          <v-row>
            <v-col
              v-for="({ src, text, title }, i) in articles"
              :key="i"
              cols="12"
              md="4"
            >
              <v-img
                :src="src"
                class="mb-4"
                height="275"
                max-width="100%"
              ></v-img>

              <h3
                class="font-weight-black mb-4 text-uppercase"
                v-text="title"
              ></h3>

              <div class="title font-weight-light mb-5" v-text="text"></div>

              <v-btn
                     class="ml-n4 font-weight-black"
                     text
                     @click="$vuetify.goTo('#contact')"
              >
                Bestill i dag
              </v-btn>
            </v-col>
          </v-row>
        </v-container>

        <div class="py-12"></div>
      </section>

      <v-sheet id="contact" color="#333333" dark tag="section" tile>
        <div class="py-12"></div>

        <v-container>
          <h2
            class="display-2 font-weight-bold mb-3 text-uppercase text-center"
          >
            Kontakt oss
          </h2>

          <v-responsive class="mx-auto mb-12" width="56">
            <v-divider class="mb-1"></v-divider>

            <v-divider></v-divider>
          </v-responsive>

          <v-theme-provider light>
            <v-row>
              <v-col cols="12">
                <v-text-field flat label="Navn*" solo></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-text-field flat label="Epost*" solo></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-text-field flat label="Emne*" solo></v-text-field>
              </v-col>

              <v-col cols="12">
                <v-textarea flat label="Melding*" solo></v-textarea>
              </v-col>

              <v-col class="mx-auto" cols="auto">
                <v-btn color="accent" x-large>
                  Send
                </v-btn>
              </v-col>
            </v-row>
          </v-theme-provider>
        </v-container>

        <div class="py-12"></div>
      </v-sheet>
    </v-content>

    <v-footer class="justify-center" color="#292929" height="100">
      <div
        class="title font-weight-light grey--text text--lighten-1 text-center"
      >
        &copy; {{ new Date().getFullYear() }} — Laget med  💜 av <a href="https://twitter.com/robaxelsen" class="skaper-link">Robert Axelsen</a>
      </div>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      articles: [
        {
          src: "/prod-1.png",
          title: "AnySharp Knivsliper 10 års garanti",
          text:
            "Suveren mekanisk knivsliper av ypperste kvalitet. Knivslipere er enkle å bruke, sørger for sikker håndtering og ikke minst freshe å se på! Med AnySharp kan enhver bli proff på kjøkkenet. For stålkniver og de fleste brødkniver med bølger/tagger."
        },
        {
          src: "/prod-2.png",
          title: "Grensaks 5-trinns med teleskoparmar",
          text:
            "5-trinns grensaks som går og forlenge skaftene på! Klipper 58mm. Går bra å slipe, bytte blad. Ergonomiske handtak i gummi. Vekt 1,5kg Lengde opptil 100 cm. Abeider i fem trinn for å enklere kunne klippe tykke grener."
        },
        {
          src: "/prod-3.png",
          title: "Cover Blubber (Matovertrekk)",
          text:
            "Matovertrekk gjør det lettere å oppbevare matrester. Bedre holdbarhet, mer miljøvennlig, og økonomisk. Prøv våre produkter i dag."
        }
      ],
      stats: [
        ["2", "Ansatte"],
        ["10+", "Produkter"],
        ["60+", "Messer"],
        ["3000", "Produkter solgt"]
      ]
    };
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
</style>
