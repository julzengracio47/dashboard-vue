<template>
  <aside
    id="sidebar"
    class="sidebar-nav d-flex flex-column justify-content-between"
    :class="{ open: toggled }"
  >
    <nav v-show="toggled" class="nav flex-column">
      <header class="sidebar-brand">
        <span><i class="bi bi-bootstrap"></i>&nbsp;Dashboard</span>
      </header>
      <div class="mb-5">
        <Sidebar-Header title="Theme" />
        <Sidebar-Item path="/" icon="bi-house-door" name="Home" />
        <Sidebar-Item path="/colors" icon="bi-droplet" name="Colors" />
        <Sidebar-Item path="/typography" icon="bi-pen" name="Typography" />
      </div>
      <div class="mb-5">
        <Sidebar-Header title="Components" />
        <Sidebar-Item path="/buttons" icon="bi-menu-button-wide-fill" name="Buttons" />
        <!-- CODE BELOW IS FOR DROPDOWN STYLE NAV -->
        <!-- <Sidebar-Dropdown
          target="forms"
          name="Forms"
          icon="bi-card-checklist"
        />
        <div class="collapse" id="forms">
          <Sidebar-Item path="/" name="Overview"/>
          <Sidebar-Item path="/" name="Form Control" />
          <Sidebar-Item path="/" name="Types &amp; Layouts" />
          <Sidebar-Item path="/" name="Validation" />
        </div> -->
      </div>
      <div class="mb-5">
        <Sidebar-Header title="External Links" />
        <Sidebar-Item path="/" icon="bi-facebook" name="Facebook" />
        <Sidebar-Item path="/" icon="bi-twitter" name="Twitter" />
        <Sidebar-Item path="/" icon="bi-linkedin" name="LinkedIn" />
      </div>
    </nav>
    <div
      v-if="toggled"
      class="justify-content-end"
      id="closeBtn"
      @click="toggleSidebar"
    >
      <div class="float-end me-3 my-2">
        <i class="bi bi-chevron-left"></i>
      </div>
    </div>
  </aside>
</template>

<script>
import sidebarItem from "./Sidebar-Item";
import sidebarHeader from "./Sidebar-Header";
// import sidebarDropdown from "./Sidebar-Dropdown";

export default {
  name: "Sidebar",
  components: {
    "Sidebar-Item": sidebarItem,
    "Sidebar-Header": sidebarHeader,
    // "Sidebar-Dropdown": sidebarDropdown,
  },
  data: function () {
    return {
      toggle: this.toggled,
      dropdownBtnClass: "d-flex justify-content-between",
    };
  },
  props: {
    toggled: Boolean,
  },
  methods: {
    toggleSidebar: function () {
      this.$emit("toggle");
    },
  },
};
</script>

<style scoped>
.open {
  width: 250px !important;
}
* {
  color: #fff;
  white-space: nowrap;
}
.sidebar-nav {
  position: fixed;
  top: 0;
  left: 0;
  overflow-x: hidden;
  background-color: #262626;
  transition: 0.5s;
  height: 100%;
  width: 0;
  z-index: 9999;
}
.sidebar-brand {
  text-align: center;
  padding: 20px;
  font-weight: bold;
  font-size: 1.3em;
}
.nav-group {
  list-style-type: none;
  padding: 0;
}

#closeBtn {
  cursor: pointer;
}
#closeBtn i {
  font-size: 1.1em;
}
#closeBtn:hover {
  background-color: #333333;
  -webkit-transition: 0.3s linear;
  -ms-transition: 0.3s linear;
  transition: 0.3s linear;
}
/* @media screen and (min-width: 992px) {
  #closeBtn {
    visibility: hidden;
  }
} */
</style>
