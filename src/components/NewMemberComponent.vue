<template>
  <div class="new-member">
    <div class="row">
      <div class="col-1">
        <router-link to="/">
          <div class="home-btn">
            <i class="fas fa-arrow-circle-left"></i>
          </div>
        </router-link>
      </div>
    </div>
    <section class="row justify-content-center">
      <div class="col-10 col-lg-10 card-block">
        <h4 class="card-title mt-4">Hej och välkommen till LIMITLESS MALMÖ!</h4>
        <hr class="hr-style" />
        <!-- <p class="content"></p> -->
        <div class="row">
          <div class="col-12">
            <ul class="unordered">
              <li class="li-item mb-2">
                Superkul att du har hittat hit och vi hoppas att du kommer
                stormtrivas hos oss. Som ny deltagare kan det ibland kännas lite
                pirrigt att delta på våra pass då det är gruppträning eller
                kanske om det är din första gång. Du kan vara SUPERLUGN, våra
                instruktörer är erfarna och vänliga och grupperna är välkomnande
                för alla nivåer, nybörjare som avancerad och åldrar (13 år och
                uppåt). Vårt fokus ligger på ditt välmående och att träning ska
                vara kul (även om det kan vara tuffa övningar ibland).
              </li>
              <br />
              <li class="li-item">
                Du får gärna komma 5-10 minuter innan passet börjar för enkel
                registrering i receptionen samt om du har frågor så kan du
                ställa dessa i lugn och ro. Efter din registrering kan du nyttja
                våra omklädningsrum med tillhörande dusch och bastu eller hänga
                lite med andra medlemmar innan passet startar. Utrustning såsom
                boxningshandskar, BJJ-dräkt mm finns att låna på plats om
                behovet finns.
              </li>
              <br />
              <li class="li-item">
                Vi har förvaringshyllor inne i träningslokalerna för dina
                ägodelar och värdesaker, lämna inget i omklädningsrummet utan ta
                med dig allt, ytterskorna ställs utanför träningslokalen och
                resterande tas med in och läggs i något av hyllfacken i lokalen.
              </li>
              <br />
              <li class="li-item">
                Våra instruktörer kommer ta hand om dig och har du frågor så
                ställ gärna dom, man kan aldrig fråga för lite! Du är välkommen
                att prova på vilka schemalagda träningspass du vill, avgiften är
                100kr som omvandlas till den obligatoriska medlemsavgiften om du
                väljer att fortsätta hos oss. Medlemsavgiften öppnar ditt
                medlemskap i föreningen samt gäller för din försäkring när du
                deltar under passen. Du erhåller 3 st prova på-tillfällen av
                valfria pass på schemat.
              </li>
              <!-- <hr class="hr-style" /> -->
              <br />
              <li class="li-item">
                Nedan hittar du information samt en bilaga för GDPR-samtycke som
                behöver vara ifylld (våran policy hittar du under knappen
                <router-link to="/om-limitless" style="color: cornflowerblue;"
                  >”OM FÖRENINGEN”</router-link
                >, skriv gärna ut GDPR-samtyckesblanketten, signera och ta med
                till LIMITLESS MALMÖ där du lämnar in bilagan ifylld. Har du
                inte möjlighet att skriva ut så finns blanketten även i
                receptionen eller hos instruktören.
              </li>
              <br />
              <li class="li-item">
                Vänligen klicka på länken där du kommer till
                <strong>”Medlemsregistreringen”</strong>, denna skall fyllas i
                korrekt oavsett vid ”prova på-pass” eller vid tecknande av
                träningskort. Är det första gången du provar på något av våra
                pass, välj ”Prova på – medlemsavgift” i ”Medlemstyp”.
              </li>
            </ul>
          </div>
        </div>
      </div>
    </section>
    <h4 class="mt-3 mb-4 sthlm-header">Medlemsregistreringen</h4>
    <section class="row justify-content-center">
      <div
        v-for="item in regMember"
        :key="item.Id"
        class="col-8 col-sm-4 mt-2 mb-5"
      >
        <a :href="item.href" class="stadgar" target="_blank">
          {{ item.name }}
          <i class="fas fa-external-link-alt ml-2"></i>
        </a>
      </div>
    </section>
    <h4 class="mt-3 mb-4 sthlm-header">SAMTYCKESBLANKETTER</h4>
    <section class="row justify-content-center">
      <div
        v-for="item in newMemberType"
        :key="item.Id"
        class="col-6 col-sm-4 mt-2 mb-5"
      >
        <a :href="item.Pdf" class="stadgar" target="_blank">
          {{ item.Name }}
          <i class="fas fa-external-link-alt ml-2"></i>
        </a>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { AboutUsModel } from "../types/AboutUsModel";
import newMemberData from "../assets/data/NewMember";
import { Component, Vue } from "vue-property-decorator";
@Component({
  components: {}
})
export default class NewMemberComponent extends Vue {
  private newMemberType: AboutUsModel[] = newMemberData;
  private regMember: any = [
    {
      id: 1,
      name: "REGISTRERA DIG HÄR",
      href: "https://member.myclub.se/pub/forms/6918/totxVl2Wlz/"
    }
  ];
}
</script>
<style scoped lang="scss">
.new-member {
  .mt-5 {
    @media only screen and (max-width: 568px) {
      margin-top: 1rem !important;
    }
  }
  .home-btn {
    color: var(--primary);
    font-size: 50px;
  }
  .home-btn:hover {
    color: var(--hover);
  }
  .card-block {
    padding: 0px 13px;
    -webkit-transition: 0.2s;
    margin: 13px;
    // max-width: 720px;
    transition: 0.2s;
    background-color: #f2f2f2;
    box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.2), 0 5px 5px 0 rgba(0, 0, 0, 0.24);
    @media only screen and (max-width: 568px) {
    }
    .hr-style {
      background-color: var(--secondary);
    }
    .card-title {
      font-weight: bolder;
      @media only screen and (max-width: 768px) {
        width: 100%;
      }
    }
    .name {
      color: var(--primary);
    }
    .unordered {
      text-align: left;

      .li-item {
        // text-decoration: none;
        // list-style: none;
        // font-size: 20px;
        text-decoration: none;
        list-style: none;
        font-size: 20px;
        width: 75%;
        margin: 0 auto;
        @media only screen and (max-width: 768px) {
          font-size: 15px;
          width: 100%;
        }
      }
    }
    .content {
      @media only screen and (max-width: 568px) {
        font-size: 13px;
      }
    }
  }
  .sthlm-header {
    text-align: center;
    background-color: var(--primary);
    color: white;
    margin: 0 auto;
    width: 50%;
    font-size: 20px;
    text-transform: uppercase;
    padding: 20px;
    line-height: 1.2;
    box-shadow: 0 1px 2px rgba(0, 0, 0, 0.7);
    @media only screen and (max-width: 768px) {
      width: 100%;
    }
  }
  .stadgar {
    font-size: 20px;
  }

  a {
    position: relative;
    color: #000;
    text-decoration: none;
  }

  a:hover {
    color: #000;
  }

  a:before {
    content: "";
    position: absolute;
    width: 100%;
    height: 2px;
    bottom: 0;
    left: 0;
    background-color: var(--secondary);
    visibility: hidden;
    -webkit-transform: scaleX(0);
    transform: scaleX(0);
    -webkit-transition: all 0.3s ease-in-out 0s;
    transition: all 0.3s ease-in-out 0s;
  }

  a:hover:before {
    visibility: visible;
    -webkit-transform: scaleX(1);
    transform: scaleX(1);
  }

  // .card-block:hover {
  //   box-shadow: 0 2px 6px 0 rgba(0, 0, 0, 0.1);
  // }
}
</style>
