<script>
    import { useLocation } from "svelte-navigator";
    import { Link } from "svelte-navigator";
    import User from "./styled__components/User.svelte";
    import SeachForm from "./SeachForm.svelte";
    const location = useLocation();

    let pathname = $location.pathname;
    const navLinks = [
      { pathname: "/", title: "Home" },
      { pathname: "/blog", title: "Blog" },
      { pathname: "/bloggers", title: "Bloggers" },
      { pathname: "/about", title: "About" },
    ];
  </script>

  <nav class="navbar fixed-top navbar-expand-md navbar-dark bg-dark">
    <div class="container">
      <a class="navbar-brand" href="/">BlogHut</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarSupportedContent"
        aria-controls="navbarSupportedContent"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon" />
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <div class="d-none d-lg-block">
          <SeachForm />
        </div>
        <ul class="navbar-nav ms-auto mb-2 mb-md-0">
          {#each navLinks as item}
            <li class="nav-item">
              <Link
                class={`nav-link ${pathname === item.pathname ? "active" : ""}`}
                aria-current="page"
                to={item.pathname}>{item.title}</Link
              >
            </li>
          {/each}
        </ul>
        <User src="" />
      </div>
    </div>
  </nav>