<template>
    <header :class="{ darkMode: isDarkMode }">
        <router-link to="/">
            <button class="title">
                <h1>Where in the world?</h1>
            </button>
        </router-link>
        <button class="theme" @click="toggleDarkMode">
            <div class="theme-image">
                <img :src="isDarkMode ? darkModeimage : lightModeimage" alt="">
            </div>
            <p>{{ isDarkMode ? 'Dark Mode' : 'Light Mode' }}</p>
        </button>
    </header>
</template>
  
<script setup>
import { useStore } from 'vuex';
import { ref } from 'vue';
import darkModeimage from '@/assets/icon/theme-dark.svg';
import lightModeimage from '@/assets/icon/theme-light.svg';

const store = useStore();

const toggleDarkMode = () => {
    store.commit('toggleDarkMode');
    console.log(`Dark Mode Toggled: ${store.state.isDarkMode ? 'On' : 'Off'}`);
    isDarkMode.value = store.state.isDarkMode;
};

const isDarkMode = ref(store.state.isDarkMode);
</script>
  
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:ital,opsz,wght@0,6..12,200;0,6..12,300;0,6..12,400;0,6..12,500;0,6..12,600;0,6..12,700;0,6..12,800;0,6..12,900;0,6..12,1000;1,6..12,200;1,6..12,300;1,6..12,400;1,6..12,500;1,6..12,600;1,6..12,700;1,6..12,800;1,6..12,900;1,6..12,1000&display=swap');

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 2rem 5rem;
    border-bottom: 3px solid rgba(99, 99, 99, 0.1);
    background-color: white;
    transition: background-color 0.3s, color 0.3s;
}

.title {
    background-color: transparent;
    border: none;
    outline: none;
    cursor: pointer;
}

.title h1 {
    font-weight: 700;
    font-size: 1.5rem;
    color: black;
}

.theme {
    width: 11%;
    height: fit-content;
    display: flex;
    background-color: transparent;
    justify-content: space-between;
    border: none;
    outline: none;
    cursor: pointer;
}

.theme-image {
    width: 1.5rem;
    height: 1.5rem;
}

.theme-image img {
    width: 100%;
    height: 100%;
}

.theme p {
    font-weight: 500;
    font-size: 1.2rem;
    color: black;
}

.darkMode {
    background-color: hsl(209, 23%, 22%);
    color: white;
}

.darkMode .title h1 {
    color: white;
}

.darkMode .theme p {
    color: white;
}

@media screen and (max-width: 768px) {
    header {
        padding: 1rem 1rem;
        padding-top: 2rem;
        padding-bottom: 2rem;
    }

    .title h1 {
        font-size: 1.2rem;
    }

    .theme {
        width: 34%;
    }

    .theme p {
        font-size: 1rem;
    }

    .theme-image {
        width: 1.2rem;
        height: 1.2rem;
    }

    .theme-image img {
        width: 100%;
        height: 100%;
    }

}

@media (min-width: 768px) and (max-width: 1024px) {

    header {
        padding: 2rem;
    }

    .title h1 {
        font-size: 1.2rem;
    }

    .theme {
        width: 17%;
    }

    .theme p {
        font-size: 1rem;
    }

    .theme-image {
        width: 1.3rem;
        height: 1.3rem;
    }

    .theme-image img {
        width: 100%;
        height: 100%;
    }


}
</style>