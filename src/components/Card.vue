<template>
  <ion-item
    v-if="nameUser"
    :routerLink="'/message/' + id"
    :detail="false"
    class="list-item"
  >
    <div slot="start"></div>
    <ion-label class="ion-text-wrap">
      <ion-img :src="avatar"></ion-img>

      <h2>
        {{ nameUser }}
        <span class="date">
          <ion-note>{{ email }}</ion-note>
        </span>
      </h2>
    </ion-label>
  </ion-item>
</template>

<script lang="ts">
import { IonItem, IonLabel, IonNote, IonImg } from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "UsersIonicCard",
  components: {
    IonItem,
    IonLabel,
    IonNote,
    IonImg,
  },
  props: {
    userData: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
  setup(props) {
    const nameUser = `${props.userData.first_name} ${props.userData.last_name}`;
    const email = `${props.userData.email}`;
    const avatar = `${props.userData.avatar}`;
    const id = `${props.userData.id}`;
    return { nameUser, email, avatar, id };
  },
});
</script>
