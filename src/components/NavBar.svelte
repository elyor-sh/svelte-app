<script>
    import {link} from "svelte-spa-router";
</script>


<nav class="navBar">
    <a use:link class="logoNavbar linkNavbar" href="/">
        Logo
    </a >
    <ul>
        <li><a use:link href="/" class="linkNavbar">Home</a></li>
        <li><a use:link href="/info" class="linkNavbar">SvelteLogo</a></li>
        <li><a use:link href="/about" class="linkNavbar">About</a></li>
    </ul>
</nav>


<style>
    nav {
        height: 70px;
        width: 100%;
        background: purple;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding-left: 15px;
    }
    ul {
        display: flex;
    }
    li {
        padding: 0px 15px;
    }

    .navBar > :global(a.linkNavbar),.navBar  ul  li > :global(a.linkNavbar) {
        text-decoration: none;
        color: #fff;
    }

    .navBar > :global(a.logoNavbar) {
        font-weight: 600;
        font-size: 18px;
    }

</style>