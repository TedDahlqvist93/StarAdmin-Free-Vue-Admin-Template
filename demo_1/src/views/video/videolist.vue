<template>
  <div>
    <b-table
      hover
      responsive
      :fields="fields"
      :items="items"
      head-variant="light"
    >
      <template #cell(name)="data">
        {{ data.value.video_title }}
      </template>

      <template #head(video_title)="data">
        <span class="text-info">{{ data.label.toUpperCase() }}</span>
      </template>

      <template #head(start_time)="data">
        <span class="text-info">{{ data.label.toUpperCase() }}</span>
      </template>

      <template #head(edit)="data">
        <span class="text-info">{{ data.label.toUpperCase() }}</span>
      </template>

      <template #head(broadcast)="data">
        <span class="text-info">{{ data.label.toUpperCase() }}</span></template
      >
      <template #head(embed)="data">
        <span class="text-info">{{ data.label.toUpperCase() }}</span>
      </template>

      <template #cell(edit)>
        <div>
          <b-button
            class="btn-fw btn-info btn-rounded"
            id="show-btn"
            @click="showEditModal"
            >Edit</b-button
          >

          <b-modal ref="my-edit-modal" hide-footer title="Edit Video">
            <div>
              <b-container fluid>
                <b-row class="my-1" v-for="type in types" :key="type">
                  <b-col sm="3">
                    <label :for="`type-${type}`"
                      >Type <code>{{ type }}</code
                      >:</label
                    >
                  </b-col>
                  <b-col sm="9">
                    <b-form-input
                      :id="`type-${type}`"
                      :type="type"
                    ></b-form-input>
                  </b-col>
                </b-row>
              </b-container>
            </div>
            <b-button class="mt-3" variant="info" @click="hideEditModal"
              >Delete</b-button
            >
            <b-button class="mt-3" variant="info" @click="hideEditModal"
              >Save</b-button
            >
            <b-button class="mt-3" variant="info" @click="hideEditModal"
              >Close</b-button
            >
          </b-modal>
        </div>
      </template>
      <template #cell(broadcast)>
        <div>
          <b-button
            class="btn-fw btn-info btn-rounded"
            id="show-btn"
            @click="showBroadcastModal"
            >Broadcast</b-button
          >

          <b-modal
            ref="my-broadcast-modal"
            hide-footer
            title="Broadcasting settings"
          >
            <div class="d-block">
              <b-container fluid>
                <b-row class="my-1" v-for="type in types" :key="type">
                  <b-col sm="3">
                    <label :for="`type-${type}`"
                      >Type <code>{{ type }}</code
                      >:</label
                    >
                  </b-col>
                  <b-col sm="9">
                    <b-form-input
                      :id="`type-${type}`"
                      :type="type"
                    ></b-form-input>
                  </b-col>
                </b-row>
              </b-container>
            </div>
            <b-button
              class="mt-3"
              variant="outline-danger"
              block
              @click="hideBroadcastModal"
              >Close Me</b-button
            >
          </b-modal>
        </div>
      </template>
      <template #cell(embed)>
        <div>
          <b-button
            class="btn-fw btn-info btn-rounded"
            id="show-btn"
            @click="showEmbedModal"
            >Generate</b-button
          >

          <b-modal ref="my-embed-modal">
            <div class="d-block text-center">
              <h3>Generate Embed code</h3>
            </div>
            <b-button
              class="mt-3"
              variant="danger"
              block
              @click="hideEmbedModal"
              >Close Me</b-button
            >
            <b-button
              class="mt-2"
              variant="outline-warning"
              block
              @click="toggleEmbedModal"
              >Toggle Me</b-button
            >
          </b-modal>
        </div>
      </template>
    </b-table>
  </div>
</template>

<script>
export default {
  methods: {
    showEditModal() {
      this.$refs["my-edit-modal"].show();
    },
    hideEditModal() {
      this.$refs["my-edit-modal"].hide();
    },
    toggleEditModal() {
      this.$refs["my-edit-modal"].toggle("#toggle-btn");
    },

    showBroadcastModal() {
      this.$refs["my-broadcast-modal"].show();
    },
    hideBroadcastModal() {
      this.$refs["my-broadcast-modal"].hide();
    },
    toggleBroadcastModal() {
      this.$refs["my-broadcast-modal"].toggle("#toggle-btn");
    },

    showEmbedModal() {
      this.$refs["my-embed-modal"].show();
    },
    hideEmbedModal() {
      this.$refs["my-embed-modal"].hide();
    },
    toggleEmbedModal() {
      this.$refs["my-embed-modal"].toggle("#toggle-btn");
    },
  },

  data() {
    return {
      types: ["text", "number", "url", "date", "time"],
      fields: ["video_title", "start_time", "edit", "broadcast", "embed"],
      items: [
        {
          video_title: "Thanksgiving Barrel Events",
          start_time: "11/28/2018 at 6:34 PM",
        },
        {
          video_title: "Christmas Barrel Events",
          start_time: "12/25/2018 at 6:34 PM",
        },
      ],
    };
  },
};
</script>
