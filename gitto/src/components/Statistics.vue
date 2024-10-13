<!-- src/components/Statistics.vue -->
<template>
    <section class="statistics mt-4">
      <div class="row">
        <div class="col-lg-4" v-for="stat in stats" :key="stat.title">
          <div :class="['box d-flex rounded-2 align-items-center mb-4 mb-lg-0 p-3', stat.bgClass]">
            <i :class="stat.icon + ' fs-2 text-center rounded-circle'"></i>
            <div class="ms-3">
              <div class="d-flex align-items-center">
                <h3 class="mb-0">{{ stat.value }}</h3>
                <span class="d-block ms-2">{{ stat.title }}</span>
              </div>
              <p class="fs-normal mb-0">{{ stat.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "Statistics-home",
    data() {
      return {
        stats: [
          {
            title: "Emails",
            value: "1,245",
            description: "Lorem ipsum dolor sit amet",
            icon: "uil-envelope-shield",
            bgClass: "bg-primary",
          },
          {
            title: "Projects",
            value: "34",
            description: "Lorem ipsum dolor sit amet",
            icon: "uil-file",
            bgClass: "bg-danger",
          },
          {
            title: "Users",
            value: "5,245",
            description: "Lorem ipsum dolor sit amet",
            icon: "uil-users-alt",
            bgClass: "bg-success",
          },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .statistics .box {
    background-color: var(--dk-dark-bg);
  }
  
  .statistics .box i {
    width: 60px;
    height: 60px;
    line-height: 60px;
    border-radius: 50%;
  }
  
  .statistics .box p {
    color: var(--dk-gray-400);
  }
  </style>
  