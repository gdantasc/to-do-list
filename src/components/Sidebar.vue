<template>
  <v-card height="100vh" width="256" class="mx-auto">
    <v-navigation-drawer permanent>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h4"
            ><v-icon x-large>{{ svgTheme }}</v-icon> To Do List
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list nav>
        <v-list-item v-for="item in items" :key="item.title" link>
          <v-list-item-icon>
            <v-icon>{{ svgPath }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title font-size="12px">{{
              item.title
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-switch
          v-model="$vuetify.theme.dark"
          inset
          label="Alterar o Tema"
          dense
          color="gray"
        ></v-switch>
      </v-list>

      <template v-slot:append>
        <div class="git">
          <a color="gray" href="https://github.com/gdantasc" target="_blank">
            <v-icon x-large>{{ svgGithub }}</v-icon>
          </a>
        </div>
      </template>
    </v-navigation-drawer>
  </v-card>
</template>

<script>
import { mdiClipboardTextOutline } from "@mdi/js";
import { mdiGithub } from "@mdi/js";
import { mdiThemeLightDark } from "@mdi/js";
export default {
  data() {
    return {
      svgPath: mdiClipboardTextOutline,
      svgGithub: mdiGithub,
      svgTheme: mdiThemeLightDark,
      items: [{ title: "Tarefas"}],
      right: null,
    };
  },
};
</script>

<style >
.git {
  text-align: center;
  margin-bottom: 25px;
}
</style>