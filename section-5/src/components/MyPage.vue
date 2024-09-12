<script setup>
</script>
<template>
    <header>
        <nav class="navbar">
            <p>Logo</p>
            <ul class="menu">
                <li><a class="item" href="#">Home</a></li>
                <li><a class="item" href="#">About</a></li>
                <li><a class="item" href="#">Contact</a></li>
            </ul>
        </nav>
    </header>
    <main class="main">
        <h1>My Page</h1>
        <p>Welcome to my page</p>
    </main>
    <footer class="footer">
        <p>© 2021 My Company</p>
    </footer>
</template>
<style scoped>
/* HEADER */

.navbar {
    background-color: #333;
    color: white;
    padding: 10px;
    display: flex;
    justify-content: space-between;
}

.menu {
    display: flex;
    list-style: none;
}

.item {
    padding: 0 1rem;
    color: white;
    text-decoration: none;
}


/* MAIN */

.main {
    padding: 2rem;
    text-align: center;
    min-height: 100vh;
}

/* FOOTER */

.footer {
    background-color: #333;
    color: white;
    padding: 1rem;
    display: flex;
    justify-content: center;
}
</style>