<template>
  <header class="header">
    <div class="logo">
      <router-link class="logo__box" to="/"
        ><img
          class="logo__img"
          src="https://github.com/michal-krawczyk10/la-tierra/blob/master/src/assets/logo.png?raw=true"
          alt="logo"
        />
        <div class="logo__text">
          <h1 class="logo__title">la Tierra</h1>
          <h2 class="logo__subtitle">pictures from Earth</h2>
        </div></router-link
      >
    </div>
    <nav class="nav" id="nav" v-bind:class="{ nav__show: isActive }">
      <router-link to="/" @click="isActive = !isActive">home</router-link
      ><span class="break">|</span
      ><router-link to="map" @click="isActive = !isActive">map</router-link>
      <span class="break">|</span>
      <router-link to="/randompic" @click="isActive = !isActive"
        >random photo</router-link
      >
      <span class="break">|</span>
      <router-link to="/about" @click="isActive = !isActive">about</router-link>
    </nav>
    <div class="ham" @click="isActive = !isActive">
      <span class="ham__line"></span>
      <span class="ham__line"></span>
      <span class="ham__line"></span>
    </div>
  </header>
  <GoBack /><span
    v-bind:class="{ background: isActive }"
    @click="isActive = !isActive"
  ></span>
</template>

<script>
import GoBack from "../components/GoBack";
export default {
  name: "Header",
  data() {
    return {
      isActive: false,
    };
  },
  components: { GoBack },
};
</script>

<style lang="scss" scoped>
* {
  transition: 0.3s ease-in-out;
}

.header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  margin: 2rem auto 0.4rem;
  width: 70vw;
  @media screen and (max-width: 1220px) {
    width: 80%;
    margin: 2rem auto 0;
  }
  @media screen and (max-width: 1024px) {
    margin: 2rem auto 2rem;
  }
}
.logo {
  width: 400px;
  @media screen and (max-width: 768px) {
    width: 240px;
  }
  &__box {
    display: flex;
    flex-direction: row;
    align-items: center;
  }
  &__img {
    width: 100px;
    margin-right: 1rem;
    @media screen and (max-width: 768px) {
      width: 64px;
    }
  }
  &__text {
    &:hover > * {
      color: var(--lt-main);
    }
    &.router-link-exact-active > * {
      color: var(--lt-main);
    }
    & > * {
      color: var(--main);
      @media screen and (max-width: 768px) {
        font-size: 1.2rem;
      }
    }
  }
  &__title {
    text-align: left;
  }
  &__subtitle {
    text-align: left;
    @media screen and (max-width: 768px) {
      text-align: left;
      font-size: 1rem;
    }
    @media screen and (max-width: 350px) {
      display: none;
    }
  }
}
.nav {
  font-size: 1.4rem;
  display: flex;
  align-items: center;
  justify-content: flex-end;
  @media screen and (max-width: 1024px) {
    font-size: 1.1rem;
  }
  @media screen and (max-width: 768px) {
    flex-direction: column;
    align-items: flex-end;
    position: fixed;
    top: 0;
    right: -200px;
    width: 200px;
    background: var(--main);
    color: var(--op-main);
    padding: 1em 0;
    border-radius: 0 0 0 16px;
    z-index: 20;
  }
  & > a {
    text-align: center;
    padding: 0 0.5em;
    &:hover {
      color: var(--lt-main);
    }
    @media screen and (max-width: 768px) {
      color: var(--op-main);
      padding: 0.5em 1.5em;
      width: 100%;
      text-align: right;
      &:hover {
        background: var(--lt-main);
        color: var(--op-main);
      }
    }
  }
  &__show {
    @media screen and (max-width: 768px) {
      position: absolute;
      right: 0;
    }
  }
}
.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  z-index: -10;
  opacity: 0;
  transition: 0.2s ease-in;
  @media screen and (max-width: 768px) {
    display: inline-block;
    z-index: 10;
    background: var(--lt-main);
    opacity: 0.4;
  }
}
.ham {
  position: absolute;
  top: 2.4rem;
  right: 3rem;
  width: 60px;
  height: 48px;
  display: none;
  flex-direction: column;
  @media screen and (max-width: 480px) {
    right: 1rem;
  }
  &__line {
    border: 4px solid var(--main);
    border-radius: 4px;
    margin: 4px;
  }
  @media screen and (max-width: 768px) {
    display: flex;
  }
  &:hover {
    cursor: pointer;
    & span {
      border: 4px solid var(--lt-main);
    }
  }
}
.break {
  @media screen and (max-width: 768px) {
    display: none;
  }
}
</style>
