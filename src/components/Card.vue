<template>
  <ion-item
    v-if="title"
    :routerLink="'/message/' + id"
    :detail="false"
    class="list-item"
  >
    <div slot="start"></div>
    <ion-label class="ion-text-wrap">
      <ion-img :src="thumbnail"></ion-img>

      <h2>
        {{ title }}
        <br />
        <span class="date">
          <ion-note>{{ short_description }}</ion-note>
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
    gameData: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
  setup(props) {
    const title = `${props.gameData.title}`;
    const short_description = `${props.gameData.short_description}`;
    const thumbnail = `${props.gameData.thumbnail}`;
    const id = `${props.gameData.id}`;
    return { title, short_description, thumbnail, id };
  },
});
</script>
