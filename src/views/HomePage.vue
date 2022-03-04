<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Inbox</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-refresher slot="fixed" @ionRefresh="refresh($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>

      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Inbox</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-list>
        <!-- <MessageListItem v-for="message in messages" :key="message.id" :message="message" /> -->
        <Card
          v-for="userData in usersData"
          :key="userData.id"
          :user-data="userData"
        />
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonContent,
  IonHeader,
  IonList,
  IonPage,
  IonRefresher,
  IonRefresherContent,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
// import MessageListItem from '@/components/MessageListItem.vue';
import Card from "@/components/Card.vue";
import { defineComponent } from "vue";
// import { getMessages } from "@/data/messages";
import { getUsersData } from "@/data/userData";

export default defineComponent({
  name: "HomePage",
  data() {
    return {
      usersData: getUsersData(),
    };
  },
  methods: {
    refresh: (ev: CustomEvent) => {
      setTimeout(() => {
        ev.detail.complete();
      }, 3000);
    },
  },
  components: {
    IonContent,
    IonHeader,
    IonList,
    IonPage,
    IonRefresher,
    IonRefresherContent,
    IonTitle,
    IonToolbar,
    Card,
    // MessageListItem,
  },
});
</script>
