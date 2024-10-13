<!-- src/components/Sidebar.vue -->
<template>
    <aside :class="['sidebar', { collapsed: isCollapsed }]" id="show-side-navigation1">
      <i
        class="uil-bars close-aside d-md-none d-lg-none"
        @click="toggleSidebar"
        data-close="show-side-navigation1"
      ></i>
      <div class="sidebar-header d-flex justify-content-center align-items-center px-3 py-4">
        <img
          class="rounded-pill img-fluid"
          width="65"
          src="https://uniim1.shutterfly.com/ng/services/mediarender/THISLIFE/021036514417/media/23148907008/medium/1501685726/enhance"
          alt="User Avatar"
        />
        <div class="ms-2">
          <h5 class="fs-6 mb-0">
            <a class="text-decoration-none" href="#">John Doe</a>
          </h5>
          <p class="mt-1 mb-0">Lorem ipsum dolor sit amet consectetur.</p>
        </div>
      </div>
  
      <div class="search position-relative text-center px-4 py-3 mt-2">
        <input
          type="text"
          class="form-control w-100 border-0 bg-transparent"
          placeholder="Search here"
        />
        <i class="fa fa-search position-absolute d-block fs-6"></i>
      </div>
  
      <ul class="categories list-unstyled">
        <li v-for="item in menuItems" :key="item.name" :class="{ 'has-dropdown': item.dropdown }">
          <a href="#" @click.prevent="toggleDropdown(item.name)">
            <i :class="item.icon"></i><span>{{ item.name }}</span>
            <span v-if="item.dropdown" class="dropdown-arrow">
              <i :class="isOpen(item.name) ? 'uil-angle-down' : 'uil-angle-left'"></i>
            </span>
          </a>
          <ul v-if="item.dropdown" :class="['sidebar-dropdown', { active: isOpen(item.name) }]" class="list-unstyled">
            <li v-for="subItem in item.subItems" :key="subItem">
              <a href="#">{{ subItem }}</a>
            </li>
          </ul>
        </li>
      </ul>
    </aside>
  </template>
  
  <script>
  export default {
    name: "SidebarHome",
    props: {
      isCollapsed: {
        type: Boolean,
        default: false,
      },
    },
    data() {
      return {
        menuItems: [
          {
            name: "Dashboard",
            icon: "uil-estate fa-fw",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "File Manager",
            icon: "uil-folder",
            dropdown: false,
          },
          {
            name: "Calendar",
            icon: "uil-calendar-alt",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "Mailbox",
            icon: "uil-envelope-download fa-fw",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "Ecommerce",
            icon: "uil-shopping-cart-alt",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "Projects",
            icon: "uil-bag",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "Settings",
            icon: "uil-setting",
            dropdown: false,
          },
          {
            name: "Components",
            icon: "uil-chart-pie-alt",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "Charts",
            icon: "uil-panel-add",
            dropdown: true,
            subItems: ["Lorem ipsum", "Ipsum dolor", "Dolor ipsum", "Amet consectetur", "Ipsum dolor sit"],
          },
          {
            name: "Maps",
            icon: "uil-map-marker",
            dropdown: false,
          },
        ],
        openMenus: [],
      };
    },
    methods: {
      toggleDropdown(name) {
        if (this.openMenus.includes(name)) {
          this.openMenus = this.openMenus.filter((menu) => menu !== name);
        } else {
          this.openMenus = [name];
        }
      },
      isOpen(name) {
        return this.openMenus.includes(name);
      },
      toggleSidebar() {
        this.$emit("toggle-sidebar");
      },
    },
  };
  </script>
  
  <style scoped>
  .sidebar {
    background-color: var(--sidebar-bg-color);
    width: var(--sidebar-width);
    transition: all 0.3s ease-in-out;
    transform: translateX(0);
    z-index: 9999999;
    position: fixed;
    top: 0;
    left: 0;
    overflow: auto;
    height: 100%;
  }
  
  .sidebar.collapsed {
    width: 80px;
  }
  
  .sidebar .close-aside {
    position: absolute;
    top: 7px;
    right: 7px;
    cursor: pointer;
    color: #eee;
  }
  
  .sidebar-header h5 a {
    color: var(--dk-gray-300);
  }
  
  .sidebar-header p {
    color: var(--dk-gray-400);
    font-size: 0.825rem;
  }
  
  .search .form-control ~ i {
    color: #2b2f3a;
    right: 40px;
    top: 22px;
  }
  
  .categories > li {
    padding: 0.7rem 1.75rem;
  }
  
  .categories li a {
    color: var(--dk-gray-400);
    text-decoration: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  
  .categories li a:hover {
    background-color: rgba(255, 255, 255, 0.1);
  }
  
  .categories li i {
    font-size: 18px;
    margin-right: 0.7rem;
    color: var(--dk-gray-500);
  }
  
  .sidebar-dropdown {
    padding-left: 30px;
    display: none;
  }
  
  .sidebar-dropdown.active {
    display: block;
  }
  
  .sidebar-dropdown li a {
    font-size: 0.85rem;
    padding: 0.5rem 0;
    display: block;
    color: var(--dk-gray-400);
  }
  
  .dropdown-arrow i {
    transition: transform 0.3s ease;
  }
  
  @media (max-width: 767px) {
    .sidebar {
      transform: translateX(-270px);
    }
  
    .sidebar.collapsed {
      transform: translateX(0);
    }
  }
  </style>
  