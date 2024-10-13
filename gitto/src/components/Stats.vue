<!-- src/components/Stats.vue -->
<template>
    <section class="statis mt-4 text-center">
      <div class="row">
        <div
          class="col-md-6 col-lg-3 mb-4 mb-lg-0"
          v-for="stat in stats"
          :key="stat.title"
        >
          <div :class="['box', stat.bgClass, 'p-3']">
            <i :class="stat.icon"></i>
            <h3>{{ stat.value }}</h3>
            <p class="lead">{{ stat.title }}</p>
          </div>
        </div>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "Stats-home",
    data() {
      return {
        stats: [
          {
            title: "Page views",
            value: "5,154",
            icon: "uil-eye",
            bgClass: "bg-primary",
          },
          {
            title: "User registered",
            value: "245",
            icon: "uil-user",
            bgClass: "bg-danger",
          },
          {
            title: "Product sales",
            value: "5,154",
            icon: "uil-shopping-cart",
            bgClass: "bg-warning",
          },
          {
            title: "Transactions",
            value: "5,154",
            icon: "uil-feedback",
            bgClass: "bg-success",
          },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .statis .box {
    position: relative;
    overflow: hidden;
    border-radius: 3px;
    color: var(--dk-gray-100);
  }
  
  .statis .box h3::after {
    content: "";
    height: 2px;
    width: 70%;
    margin: auto;
    background-color: rgba(255, 255, 255, 0.12);
    display: block;
    margin-top: 10px;
  }
  
  .statis .box i {
    position: absolute;
    height: 70px;
    width: 70px;
    font-size: 22px;
    padding: 15px;
    top: -25px;
    left: -25px;
    background-color: rgba(255, 255, 255, 0.15);
    line-height: 60px;
    text-align: right;
    border-radius: 50%;
  }
  </style>
  