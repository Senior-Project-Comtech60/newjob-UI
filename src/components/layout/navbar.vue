/* eslint-disable prettier/prettier */
<template>
  <div class="bg">
    <div class="position-relative">
      <b-navbar toggleable="lg" class="container">
        <b-navbar-brand>
          <router-link to="/">
            <img
              src="@/assets/Sign_language_C.svg.png"
              width="40"
              height="40"
              alt=""
            />
          </router-link>
        </b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item to="/">JOBCT</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-nav-item to="/" right>{{ $t("global.home") }}</b-nav-item>
            <b-nav-item to="/PageSearch" right>{{
              $t("global.search")
            }}</b-nav-item>
            <b-nav-item-dropdown
              class="font-sizez my-auto"
              :text="`${language}`"
              right
            >
              <b-dropdown-item @click="toggleSelectLanguage('th')"
                >TH</b-dropdown-item
              >
              <b-dropdown-item @click="toggleSelectLanguage('en')"
                >EN</b-dropdown-item
              >
            </b-nav-item-dropdown>

            <b-nav-item-dropdown right>
              <!-- Using 'button-content' slot -->
              <template #button-content>
                <img
                  src="/images/user-5865.svg"
                  width="20"
                  height="20"
                  alt=""
                  title="Login"
                />
              </template>
              <b-dropdown-item
                ><router-link to="/PageLogin"
                  ><p>{{ $t("global.signIn") }}</p></router-link
                ></b-dropdown-item
              >
              <b-dropdown-item
                ><router-link to="/"
                  ><p>{{ $t("global.signOut") }}</p></router-link
                ></b-dropdown-item
              >
            </b-nav-item-dropdown>
          </b-navbar-nav>
        </b-collapse>
      </b-navbar>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import { Locale, Language } from "@/locales/Locale";
export default Vue.extend({
  data() {
    const language = Locale.currentLanguage;
    return { language };
  },
  computed: {
    selectedLanguage() {
      const th =
        this.language === "th"
          ? "btn btn-sm btn-secondary"
          : "btn btn-sm btn-light";
      const en =
        this.language === "en"
          ? "btn btn-sm btn-secondary"
          : "btn btn-sm btn-light";

      return { th, en };
    }
  },
  watch: {
    language(value) {
      Locale.currentLanguage = value;
    }
  },
  methods: {
    toggleSelectLanguage(lang) {
      // this.isLanguage = lang;
      if (lang === "th") {
        this.language = Language.Thai;
      }
      if (lang === "en") {
        this.language = Language.English;
      }
      if (lang === "de") {
        this.language = Language.German;
      }
    }
  }
});
</script>
<style lang="scss" scoped>
nav {
  background-color: rga(251, 251, 252, 255);
}
// box-shadow: 0px 4px 8px #00c2fdf3;
b-nav-item {
  color: black;
}
.font-sizez {
  font-size: 16px;
  font-weight: 400;
  font-stretch: normal;
  font-style: normal;
  line-height: 1;
  letter-spacing: normal;
}
b-navbar {
  position: fixed;
}
.bg {
  position: fixed;
  width: 100%;
  top: 0;
  background-color: rgb(255, 255, 255);
  box-shadow: rgba(131, 185, 202, 0.466) 0px 2px 8px 0px;
  z-index: 100;
  position: sticky;
}
</style>
