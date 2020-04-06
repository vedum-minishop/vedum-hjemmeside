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
            og skylles lett av med såpe og vann. De er helt super. Rosesakser,
            grensakser 3 trinns små / 5 trinns store, topp sager, topp sakser 3
            trinns med mer fra RP Demo som har eksistert i mer enn 30 år og
            selges kun på messer og marknader.
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
                md="4"
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
              v-for="({ src, text, title, price }, i) in articles"
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

              <h4
                class="font-weight-black mb-4"
                v-text="'Kroner ' + price + ' + evt frakt'"
              ></h4>

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
            <v-form name="kontaktskjema" ref="form" v-model="valid" action="/takk/" method="POST" lazy-validation data-netlify="true">
              <input type="hidden" name="form-name" value="kontaktskjema" />
              <v-row>
                <v-col cols="12">
                  <v-text-field
                    name="navn"
                    v-model="navn"
                    type="text"
                    flat
                    label="Navn*"
                    solo
                  ></v-text-field>
                </v-col>

                <v-col cols="12">
                  <v-text-field
                    name="epost"
                    type="email"
                    v-model="epost"
                    flat
                    label="Epost*"
                    solo
                  ></v-text-field>
                </v-col>

                <v-col cols="12">
                  <v-text-field
                    name="emne"
                    type="text"
                    v-model="emne"
                    flat
                    label="Emne*"
                    solo
                  ></v-text-field>
                </v-col>

                <v-col cols="12">
                  <v-textarea
                    name="melding"
                    type="text"
                    v-model="melding"
                    label="Melding*"
                    solo
                  ></v-textarea>
                </v-col>

                <v-col class="mx-auto" cols="auto">
                  <v-btn color="accent" x-large type="submit">
                    Send
                  </v-btn>
                </v-col>
              </v-row>
            </v-form>
          </v-theme-provider>
        </v-container>

        <div class="py-12"></div>
      </v-sheet>
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
  export default {
    data() {
      return {
        valid: true,
        navn: "",
        epost: "",
        emne: "",
        melding: "",
        articles: [
          {
            src: "/produkt-anysharp.png",
            title: "AnySharp Knivsliper 10 års garanti",
            price: 350,
            text:
              "Suveren mekanisk knivsliper av ypperste kvalitet. Knivslipere er enkle å bruke, sørger for sikker håndtering og ikke minst freshe å se på! Med AnySharp kan enhver bli proff på kjøkkenet. For stålkniver og de fleste brødkniver med bølger/tagger."
          },
          {
            src: "/produkt-grensaks-5trinns.png",
            title: "Grensaks 5-trinns med teleskoparmar",
            price: 600,
            text:
              "5-trinns grensaks som går og forlenge skaftene på! Klipper 58mm. Går bra å slipe, bytte blad. Ergonomiske handtak i gummi. Vekt 1,5kg Lengde opptil 100 cm. Abeider i fem trinn for å enklere kunne klippe tykke grener."
          },
          {
            src: "/produkt-matovertrekk.png",
            title: "Cover Blubber (Matovertrekk)",
            price: 299,
            text:
              "Matovertrekk gjør det lettere å oppbevare matrester. Bedre holdbarhet, mer miljøvennlig, og økonomisk. Prøv våre produkter i dag."
          },
          {
            src: "/produkt-grensaks.png",
            title: "Grensaks 3 trinn",
            price: 259,
            text:
              "Kjempebra grensaks og bladet kan skiftes ut når det er utslitt. Artikkelnummer 3101-TW. Våre bestselgende grensakser! Kan kutte opp til 24 mm. Grensaksen er i metall. Har en utvesksling som fordeler kraften på opptil tre trinn ut i fra hvor tykk grenen er. Før å klippe tynne grener i ett klipp benyttes toppen på grensaksen. Bladet kan slipes eller byttes når den er slitt."
          },
          {
            src: "/produkt-japanskslipt-handsag.png",
            title: "Handsag Japanskslipt 16cm",
            price: 259,
            text:
              "En liten men extremt effektiv! Enkel å ta i hop, smidig å ha med på jakt og fiske eller når man skal klatre i tre."
          },
          {
            src: "/produkt-rosesaks.png",
            title: "Rose saks",
            price: 259,
            text:
              "Verdens beste idé! Slippe å stikke seg på taggrne for denne rosesaksen holder igjen grenen så du enkelt kan legge den direkte i bosset eller trillebåren. Bladet kan slipes. Klipper 10mm."
          },
          {
            src: "/produkt-teleskopskaft.png",
            title: "3, 6 meter telskopskaft",
            price: 600,
            text:
              "Teleskopskaft i glasfiber fra 202 cm til 360 cm. Låser skaftet på lengden du vil ha ved å vri på øverste delen."
          },
          {
            src: "/produkt-japanskslipt-sag.png",
            title: "Japanskslipt sag",
            price: 700,
            text:
              "Japanskslipt sag med kniver oppe og nede på sagbladet slik at den ikke detter av grenen når du sager. Knivene skjærer bark som evt henger igjen. Bladet er lager av karbonstål som holder i lang tid og er stiv. Sager tykke grener på kort tid."
          },
          {
            src: "/produkt-toppsaks.png",
            title: "Topp saks 3-trinn med sag",
            price: 700,
            text:
              "Toppsaks som klipper i tre trinn for at du kan klippe tykkere grener. Det går å klippe uten flere trinn. Sagen monteres enkelt fast med en vingemutter. Bladet kan slipes."
          }
        ],
        stats: [
          ["10+", "Produkter"],
          ["60+", "Messer"],
          ["12000+", "Produkter solgt"]
        ]
      };
    },
    mounted() {
      document.title = "Vedum Minishop AS";
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
