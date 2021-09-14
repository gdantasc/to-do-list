<template>
  <div>
    <template>
      <v-row justify="center">
        <v-dialog v-model="dialog" persistent max-width="600px">
          <template v-slot:activator="{ on, attrs }">
            <v-icon v-bind="attrs" v-on="on">
              {{ SvgPencil }}
            </v-icon>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">Editar Tarefas</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12" sm="6" md="4">
                    <v-text-field label="Nome" required></v-text-field>
                  </v-col>
                  <v-col cols="12" sm="10" md="10">
                    <v-text-field
                      label="Descrição"
                      hint="Insira uma descrição pra sua tarefa"
                    ></v-text-field>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>

              <v-btn color="blue darken-1" text @click="dialog = false">
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>
    </template>
  </div>
</template>

<script>
import { mdiPencil } from "@mdi/js";
export default {
  props: {
    tasks: {type: Array, required: true},
  },
  data: () => ({
    dialog: false,
    SvgPencil: mdiPencil,
  }),
};
</script>

<style>
</style>