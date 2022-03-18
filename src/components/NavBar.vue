<template>
  <header :class="{ 'scrolled-nav': scrolledNav }">
    <nav>
      <div class="branding">
        <svg width="56" height="56" viewBox="0 0 200 156" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M198.844 37.5686L135.757 0.294468C135.076 -0.105141 134.235 -0.0966383 133.563 0.311473L99.9448 20.9296L66.3267 0.319975C65.655 -0.0966383 64.8133 -0.0966383 64.1331 0.30297L1.04592 37.5686C0.399744 37.9512 0.00863817 38.6399 0.00013586 39.3881C-0.00836645 40.1363 0.38274 40.825 1.02041 41.2161L34.0179 61.3751L9.52273 76.4072C9.36968 76.5007 9.23365 76.6027 9.11461 76.7302C8.96157 76.8918 8.83404 77.0788 8.73201 77.2829V77.2914C8.62148 77.538 8.56196 77.793 8.54496 78.0736C8.54496 78.0736 8.54496 78.0736 8.54496 78.0821C8.54496 78.0821 8.54496 78.0821 8.54496 78.0906C8.54496 78.0991 8.54496 78.0906 8.54496 78.0991C8.54496 78.0991 8.54496 78.0991 8.54496 78.1076V153.6C8.54496 153.804 8.57047 154.016 8.62998 154.22C8.698 154.467 8.81703 154.696 8.96157 154.9C9.14862 155.147 9.37819 155.351 9.64176 155.496C9.89683 155.64 10.1774 155.725 10.4835 155.751C10.5515 155.759 10.611 155.759 10.679 155.759C10.8746 155.759 11.0701 155.734 11.2657 155.674C11.4613 155.615 11.6483 155.53 11.8183 155.428L73.8937 117.499C74.2338 117.482 74.5739 117.38 74.88 117.193L100.004 101.863L125.129 117.193C125.435 117.38 125.766 117.482 126.115 117.499L188.19 155.428C188.352 155.53 188.539 155.615 188.726 155.674C188.921 155.734 189.126 155.759 189.321 155.759C189.389 155.759 189.449 155.759 189.517 155.751C189.823 155.725 190.112 155.632 190.367 155.487C190.622 155.343 190.852 155.147 191.03 154.9C191.175 154.696 191.294 154.475 191.362 154.22C191.421 154.016 191.447 153.804 191.447 153.6V78.2182V78.2097C191.447 78.2097 191.447 78.2097 191.447 78.2012C191.447 78.1926 191.447 78.2012 191.447 78.1926C191.43 77.8866 191.353 77.589 191.217 77.3254C191.158 77.2234 191.098 77.1214 191.022 77.0278C191.022 77.0278 191.022 77.0278 191.013 77.0193C190.869 76.8408 190.681 76.6877 190.477 76.5602L165.982 61.5366L198.98 41.3776C199.617 40.9865 200 40.2978 200 39.5496C200 38.8014 199.49 37.9512 198.844 37.5686ZM132.679 5.85498V41.0205L104.017 23.4378L132.679 5.85498ZM136.93 48.6131L157.735 61.3751L136.93 74.086V48.6131ZM67.2194 46.0029L99.9533 25.9289L132.687 46.0029V76.6792L99.9533 96.6767L67.2194 76.6792V46.0029ZM95.8807 23.4378L67.2194 41.012V5.85498L95.8807 23.4378ZM6.24933 39.4306L62.9598 5.9315V43.6222L38.082 58.8839L6.24933 39.4306ZM62.9683 48.6131V74.086L42.1631 61.3751L62.9683 48.6131ZM12.7536 149.952V81.9422L69.345 115.373L12.7536 149.952ZM73.4516 112.865L14.7516 78.1841L38.0905 63.8663L63.2148 79.2129C63.3934 79.5445 63.6569 79.8251 63.98 80.0292L95.6086 99.3294L73.4516 112.865ZM187.136 149.952L130.545 115.373L187.136 81.9422V149.952ZM185.146 78.1841L126.438 112.865L104.281 99.3294L135.91 80.0292C136.241 79.8251 136.505 79.5445 136.675 79.2129L161.799 63.8663L185.146 78.1841ZM161.808 58.8839L136.93 43.6222V5.9315L193.64 39.4306L161.808 58.8839Z" fill="black"/>
</svg>

      </div>
      <ul v-show="!mobile" class="navigation">
        <li>
          <router-link class="link" :to="{name: 'Home'}">Home</router-link>
        </li>
        <li>
          <router-link class="link" :to="{name: 'Explore'}">Explore</router-link>
        </li>
        <li>
          <router-link class="link" :to="{name: 'Register'}">Register</router-link>
        </li>
        <li>
          <router-link v-if="!jwt" class="link" :to="{name: 'Login'}">Login</router-link>
        </li>
        <li>
          <router-link :to="{name: 'Login'}" @click="logout"><i
              class="fa-solid fa-right-from-bracket"></i></router-link>
        </li>
      </ul>
      <div class="icon">
        <i @click="toggleMobileNav" v-show="mobile" class="fa fa-bars" :class="{'icon-active' : mobileNav}"></i>
      </div>
      <transition name="mobile-nav">
        <ul v-show="mobileNav" class="dropdown-nav pt-4">
          <li>
            <router-link class="link" :to="{name: 'Home'}">Home</router-link>
          </li>
          <li>
            <router-link class="link" :to="{name: 'Explore'}">Explore</router-link>
          </li>
          <li>
            <router-link class="link" :to="{name: 'Register'}">Register</router-link>
          </li>
          <li>
            <router-link class="link" :to="{name: 'Login'}">Login</router-link>
          </li>
          <li>
            <router-link id="logout" :to="{name: 'Login'}" @click="logout"><i
                class="fa-solid fa-right-from-bracket"></i></router-link>
          </li>
        </ul>
      </transition>
    </nav>
  </header>
  <router-view v-slot="{ Component }">
    <transition name="route" mode="out-in">
      <component :is="Component"></component>
    </transition>
  </router-view>
</template>

<script>
  export default {
    props() {
      Loggedin
    },
    name: "navigation",
    data() {
      return {
        scrolledNav: null,
        mobile: null,
        mobileNav: null,
        windowWidth: null,
        jwt: null
      };
    },
    created() {
      window.addEventListener('resize', this.checkScreen);
      this.checkScreen();
    },
    mounted() {
      window.addEventListener('scroll', this.updateScroll)
    },
    methods: {
      toggleMobileNav() {
        this.mobileNav = !this.mobileNav;
      },

      updateScroll() {
        const scrollPosition = window.scrollY;
        if (scrollPosition > 50) {
          this.scrolledNav = true;
          return;
        }
        this.scrolledNav = false;
      },

      checkScreen() {
        this.windowWidth = window.innerWidth;
        if (this.windowWidth <= 780) {
          this.mobile = true;
          return;
        }
        this.mobile = false;
        this.mobileNav = false;
        return;
      },

      logout() {
        localStorage.clear();
        this.jwt = null;
      }
    }
  }
</script>

<style lang="scss" scoped>
  header {
    background-color: rgba(255, 255, 255, 0.8);
    z-index: 99;
    width: 100%;
    position: fixed;
    transition: .5s ease all;
    color: #fff;

    .fa-bars:before,
    .fa-navicon:before {
      color: #000;
    }

    nav {
      position: relative;
      display: flex;
      flex-direction: row;
      padding: 12px 0;
      transition: .5s ease all;
      width: 90%;
      margin: 0 auto;

      @media (min-width: 1140px) {
        max-width: 1140px;
      }

      ul,
      link {
        font-weight: 500;
        color: #fff;
        list-style: none;
        text-decoration: none;
      }

      li {
        text-transform: uppercase;
        padding: 16px;
        margin-left: 15px;
      }

      .link {
        color: #000;
        font-size: 14px;
        transition: .5s ease all;
        padding-bottom: 4px;
        border-bottom: 1px solid transparent;
        text-decoration: none;
        font-weight: 600;

        &:hover {
          color: #000;
          border-color: #000;
        }
      }

      .branding {
        display: flex;
        align-items: center;

        img {
          width: 50px;
          transition: .5s ease all;
        }
      }

      .navigation {
        display: flex;
        align-items: center;
        flex: 1;
        justify-content: flex-end;
      }

      .icon {
        display: flex;
        align-items: center;
        position: absolute;
        top: 0;
        right: 24px;
        height: 100%;

        i {
          cursor: pointer;
          font-size: 24px;
          transition: .8s ease all;
        }
      }
                  .fa-right-from-bracket {
                    color: #000 !important;
                  }

      .icon-active {
        transform: rotate(180deg);
      }

      .dropdown-nav {
        display: flex;
        flex-direction: column;
        position: fixed;
        width: 100%;
        max-width: 250px;
        height: 100%;
        // background-color: #fff;
        top: 0;
        left: 0;
        background-image: url("@/assets/images/ocean.jpg");
        background-position: center;
        background-size: cover;

        li {
          margin-left: 0;

          .link {
            color: #000;

            &:hover {
              color: #000;
              border-color: #000;
            }
          }

        }

        #logout {
          position: absolute;
          bottom: 2em;
          left: 2em;
          font-size: 1.5em;
        }
      }

      .mobile-nav-enter-active,
      .mobile-nav-leave-active {
        transition: 1s ease all;
      }

      .mobile-nav-enter-from,
      .mobile-nav-leave-to {
        transform: translateX(-250px);
      }

      .mobile-nav-enter-to {
        transform: translateX(0);
      }
    }
  }

  .scrolled-nav {
    background-color: #fff;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);

    nav {
      padding: 8px 0;


    }
  }

  .route-enter-from {
    opacity: 0;
    transform: translateX(100px);
  }

  .route-enter-active {
    transition: all 0.3s ease-out;
  }

  .route-leave-to {
    opacity: 0;
    transform: translateX(-100px);
  }

  .route-leave-active {
    transition: all 0.3s ease-in;
  }

  nav a.router-link-exact-active {
    color: #000 !important;
    border-color: #000;

    @media (max-width: 780px) {
      color: #000 !important;
      border-color: #000;
    }

  }
</style>