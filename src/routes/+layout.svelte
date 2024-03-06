<nav>
    <div class="nav-container">
        <a href="/" class="nav-logo" title="Back to Homepage">Данил Чижма</a>
        <div class="nav-links">
            {#if link.isShow}
            <a href={link.href} class="link">{link.title}</a>
            {/if}
        </div>
    </div>
</nav>

<div class="container">
    <!-- Pages will be injected below -->
    <slot></slot>
</div>

<style>
    .container {
        max-width: 1400px;
        margin: 50px auto;
    }

    .link {
        margin-right: 10px;
        transition: 0.8s ease;
    }

    .link:hover {
        border-bottom: 2px solid black;
    }
</style>

<script>
    const nav = [
        {
            title: 'Обо мне',
            href: '/about',
            isShow: false,
        },
        {
            title: 'Блог',
            href: '/blog',
            isShow: false,
        },
        {
            title: 'Портфолио',
            href: '/project',
            isShow: false,
        },
        {
            title: 'Контакты',
            href: '/contact',
            isShow: false,
        },
        {
            title: 'temp',
            href: '/temp',
            isShow: false,
        }
    ]
</script>