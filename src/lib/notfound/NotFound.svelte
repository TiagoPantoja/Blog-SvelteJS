<script>
    import { Link } from "svelte-navigator";
  </script>

  <div class="container">
    <p><b>Erro 404</b> | Página não existe</p>
    <Link to="/">Visite a página inicial</Link>
  </div>

  <style>
    .container {
      position: absolute;
      top: 50%;
      text-align: center;
      transform: translateY(-50%);
    }
  </style>