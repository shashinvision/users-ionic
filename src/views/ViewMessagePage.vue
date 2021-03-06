<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-buttons slot="start">
          <ion-back-button
            :text="getBackButtonText()"
            default-href="/"
          ></ion-back-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true" v-if="game">
      <ion-item>
        <ion-icon :icon="personCircle" color="primary"></ion-icon>
        <ion-label class="ion-text-wrap">
          <h2>
            {{ game.title }}
            <br />
            <span class="date">
              <ion-note>{{ game.platform }}</ion-note
              >&nbsp;|&nbsp;&nbsp;
              <ion-note>{{ game.genre }}</ion-note>
            </span>
          </h2>
        </ion-label>
      </ion-item>

      <div class="ion-padding">
        <h1>{{ game.title }}</h1>
        <ion-img :src="game.thumbnail"></ion-img>
        <p>{{ game.short_description }}</p>
        <a :href="game.freetogame_profile_url">{{
          game.freetogame_profile_url
        }}</a>
        <br />
        <a :href="game.game_url">{{ game.game_url }}</a>
        <p>{{ game.short_description }}</p>
        <p>{{ game.publisher }}</p>
        <p>{{ game.developer }}</p>
        <p>{{ game.release_date }}</p>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { useRoute } from "vue-router";
import {
  IonBackButton,
  IonButtons,
  IonContent,
  IonHeader,
  IonIcon,
  IonItem,
  IonLabel,
  IonNote,
  IonPage,
  IonToolbar,
  IonImg,
} from "@ionic/vue";
import { personCircle } from "ionicons/icons";
// import { getMessage } from '../data/messages';
import { getGameData } from "../data/gameData";
import { defineComponent } from "vue";

export default defineComponent({
  name: "ViewMessagePage",
  data() {
    return {
      personCircle,
      getBackButtonText: () => {
        const win = window as any;
        const mode = win && win.Ionic && win.Ionic.mode;
        return mode === "ios" ? "Inbox" : "";
      },
    };
  },
  setup() {
    const route = useRoute();
    const game = getGameData(parseInt(route.params.id as string, 10));

    return { game };
  },
  components: {
    IonBackButton,
    IonButtons,
    IonContent,
    IonHeader,
    IonIcon,
    IonItem,
    IonLabel,
    IonNote,
    IonPage,
    IonToolbar,
    IonImg,
  },
});
</script>

<style scoped>
ion-item {
  --inner-padding-end: 0;
  --background: transparent;
}

ion-label {
  margin-top: 12px;
  margin-bottom: 12px;
}

ion-item h2 {
  font-weight: 600;
}

ion-item .date {
  float: right;
  align-items: center;
  display: flex;
}

ion-item ion-icon {
  font-size: 42px;
  margin-right: 8px;
}

ion-item ion-note {
  font-size: 15px;
  margin-right: 12px;
  font-weight: normal;
}

h1 {
  margin: 0;
  font-weight: bold;
  font-size: 22px;
}

p {
  line-height: 22px;
}
</style>
