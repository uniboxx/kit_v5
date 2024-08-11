<script>
  // import { base } from 'app/paths';
</script>

<h1>Titolo della Pagina</h1>
<nav>
  <ul>
    <li><a href="/kit_v5">Home</a></li>
    <li><a href="/about">About</a></li>
    <li><a href="/contact">Contact</a></li>
    <li><a href="/more">More</a></li>
  </ul>
</nav>

<style lang="scss">
  nav {
    padding: 1rem;
    ul {
      list-style: none;
      display: flex;
      align-items: center;
      gap: 4rem;
      li {
        a {
          background-color: #123456;
          padding: 0.5rem 1rem;
          text-decoration: none;
          color: #eee;
          border-radius: 10px;
        }
      }
    }
  }
</style>
