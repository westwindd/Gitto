<!-- src/components/Admins.vue -->
<template>
    <section class="admins mt-4">
      <div class="row">
        <div class="col-md-6" v-for="(group, index) in adminGroups" :key="index">
          <div class="box">
            <div
              class="admin d-flex align-items-center rounded-2 p-3 mb-4"
              v-for="admin in group" :key="admin.name"
            >
              <div class="img">
                <img
                  class="img-fluid rounded-pill"
                  width="75"
                  height="75"
                  :src="admin.avatar"
                  :alt="admin.name"
                />
              </div>
              <div class="ms-3">
                <h3 class="fs-5 mb-1">{{ admin.name }}</h3>
                <p class="mb-0">{{ admin.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "Admins-home",
    data() {
      return {
        adminGroups: [
          [
            {
              name: "Joge Lucky",
              avatar: "https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148906966/small/1501685402/enhance",
              description: "Lorem ipsum dolor sit amet consectetur elit.",
            },
            {
              name: "Jane Smith",
              avatar: "https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148907137/small/1501685404/enhance",
              description: "Lorem ipsum dolor sit amet consectetur elit.",
            },
            {
              name: "Mike Johnson",
              avatar: "https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148907019/small/1501685403/enhance",
              description: "Lorem ipsum dolor sit amet consectetur elit.",
            },
          ],
          [
            {
              name: "Sara Wilson",
              avatar: "https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148907114/small/1501685404/enhance",
              description: "Lorem ipsum dolor sit amet consectetur elit.",
            },
            {
              name: "Tom Brown",
              avatar: "https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148907086/small/1501685404/enhance",
              description: "Lorem ipsum dolor sit amet consectetur elit.",
            },
            {
              name: "Emily Davis",
              avatar: "https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148907008/medium/1501685726/enhance",
              description: "Lorem ipsum dolor sit amet consectetur elit.",
            },
          ],
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .admins .box .admin {
    background-color: var(--dk-dark-bg);
  }
  
  .admins .box h3 {
    color: var(--dk-gray-300);
  }
  
  .admins .box p {
    color: var(--dk-gray-400);
  }
  </style>
  