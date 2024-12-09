<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});

function handleImageError() {
    document.getElementById('screenshot-container')?.classList.add('!hidden');
    document.getElementById('docs-card')?.classList.add('!row-span-1');
    document.getElementById('docs-card-content')?.classList.add('!flex-row');
    document.getElementById('background')?.classList.add('!hidden');
}
</script>

<template>
    <Head title="Welcome" />
    <div class="min-h-screen flex flex-col items-center justify-between text-white">
        <!-- Header Section -->
        <header class="w-full flex justify-between items-center p-6 backdrop-blur-md bg-black">
            <a href="/"><img src="https://www.databank.lv/assets/images/logo.png" alt="Databank" class="h-10" /></a>
            <nav v-if="canLogin" class="flex space-x-4">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="nav-link"
                >
                    Go to main page
                </Link>
                <template v-else>
                    <Link :href="route('login')" class="nav-link">Log in</Link>
                    <Link
                        v-if="canRegister"
                        :href="route('register')"
                        class="nav-link"
                    >
                        Register
                    </Link>
                </template>
            </nav>
        </header>

        <!-- Main Content -->
        <main class="flex-grow flex items-center justify-center text-center">
            <div>
                knkjhjhbjhj
                <h1 class="text-5xl font-extrabold drop-shadow-lg">Welcome to Portal</h1>
                <p class="text-lg mt-4 max-w-2xl drop-shadow-md">
                    Your data at your fingertips with Laravel {{ laravelVersion }} and PHP {{ phpVersion }}.
                </p>
            </div>
        </main>

        <!-- Footer Section -->
        <footer class="w-full text-center py-4 backdrop-blur-md bg-black">
            <p class="text-sm text-red-700">
                Powered by Laravel v{{ laravelVersion }} and PHP v{{ phpVersion }}
            </p>
        </footer>
    </div>
</template>

<style scoped>
/* Rainbow background for the entire page */
body {
    margin: 0;
    padding: 0;
    background: linear-gradient(124deg, #ff2400, #e81d1d, #e8b71d, #e3e81d, #1de840, #1ddde8, #2b1de8, #dd00f3, #dd00f3);
    background-size: 1800% 1800%;
    animation: rainbow 18s ease infinite;
    color: white;
    font-family: 'Arial', sans-serif;
}

/* Gradient keyframes */
@keyframes rainbow {
    0% {
        background-position: 0% 82%;
    }
    50% {
        background-position: 100% 19%;
    }
    100% {
        background-position: 0% 82%;
    }
}

/* Navigation links */
.nav-link {
    padding: 0.5rem 1rem;
    border: 2px solid gray;
    border-radius: 0.5rem;
    background-color: gold;
    color: white;
    text-decoration: none;
    font-weight: bold;
    transition: all 0.3s ease;
}

.nav-link:hover {
    background-color: rgba(31, 119, 227, 0.776);
    color: rgb(255, 255, 255);
}

main {
    width: 100vw;
    height: 50vh;
    background: linear-gradient(124deg, #ff2400, #e81d1d, #e8b71d, #e3e81d, #1de840, #1ddde8, #2b1de8, #dd00f3, #dd00f3);
    background-size: 1800% 1800%;
    animation: rainbow 18s ease infinite;
    flex-grow: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;;
}

/* Responsive design */
@media (max-width: 640px) {
    h1 {
        font-size: 3xl;
    }
    .nav-link {
        padding: 0.5rem;
        font-size: 0.875rem;
    }
}
</style>