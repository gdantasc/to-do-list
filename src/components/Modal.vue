<template>
  <div>
    <template>
      <v-row justify="center">
        <v-dialog v-model="dialog" max-width="600px" persistent>
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
                  <v-col cols="12" md="4" sm="6">
                    <v-text-field label="Nome" required></v-text-field>
                  </v-col>
                  <v-col cols="12" md="10" sm="10">
                    <label>Descrição</label>
                    <v-textarea
                        v-model="description"
                        placeholder="Insira uma Descrição para sua tarefa"
                        auto-grow
                    ></v-textarea>
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
import {mdiPencil} from "@mdi/js";

export default {
  props: {
    tasks: {type: Array, required: true},
  },
  data: () => ({
    dialog: false,
    SvgPencil: mdiPencil,
    description: '',
  }),
};
</script>

<style>
</style>