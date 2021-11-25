<script>
    import {Router, Link } from "svelte-routing";
</script>

<Router>
<nav class="navBar">
    <Link class="logoNavbar linkNavbar" to="">
        Logo
    </Link>
    <ul>
        <li><Link to="" class="linkNavbar">Home</Link></li>
        <li><Link to="info" class="linkNavbar">SvelteLogo</Link></li>
        <li><Link to="about" class="linkNavbar">About</Link></li>
    </ul>
</nav>
</Router>

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