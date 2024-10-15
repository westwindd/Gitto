<template>
    <div class="dashboard">
      <Navbar />
      <div class="content-wrapper">
        <div class="welcome-section">
          <h1>Welcome, João Paulo!</h1>
          <p>Explore the dashboard and interact with the cards below.</p>
        </div>
        <div class="gallery">
          <div class="card" v-for="(image, index) in images" :key="index" @click="handleClick(index)">
            <img :src="image.src" :alt="image.alt" />
            <div class="card-overlay">
              <p>{{ image.title }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import Navbar from "../components/Navbar.vue";
  
  export default {
    name: "DashboardHome",
    components: {
      Navbar,
    },
    data() {
      return {
        images: [
          { src: "https://via.placeholder.com/150", alt: "Image 1", title: "Card 1" },
          { src: "https://via.placeholder.com/150", alt: "Image 2", title: "Card 2" },
          { src: "https://via.placeholder.com/150", alt: "Image 3", title: "Card 3" },
          { src: "https://via.placeholder.com/150", alt: "Image 4", title: "Card 4" },
        ],
      };
    },
    methods: {
      handleClick(index) {
        console.log("Card clicked:", index);
        // Perform action on click
      },
    },
  };
  </script>
  
  <style scoped>
  .dashboard {
    display: flex;
    background: #212529;
  }
  
  .content-wrapper {
    flex-grow: 1;
    padding: 20px;
    margin-left: 80px; /* Adjust to sidebar width to prevent overlap */
    padding-left: 10vh;

  }
  
  .welcome-section {
    background: rgba(0, 0, 0, 0.1); /* Black tonality with 50% opacity */
    padding: 20px;
    color: white;
    border-radius: 8px;
    margin-bottom: 20px;
    width: 100%;
    text-align: left;
  }
  
  .welcome-section h1 {
    margin: 0;
    font-size: 2rem;
  }
  
  .welcome-section p {
    margin: 5px 0 0;
    font-size: 1rem;
  }
  
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    width: 100%;
  }
  
  .card {
    position: relative;
    cursor: pointer;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease;
  }
  
  .card:hover {
    transform: scale(1.05);
  }
  
  .card img {
    width: 100%;
    height: 180px;
    object-fit: cover;
  }
  
  .card-overlay {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(0, 0, 0, 0.5);
    color: white;
    text-align: center;
    padding: 10px;
  }
  </style>
  