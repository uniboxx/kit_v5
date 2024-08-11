<script>
  import { resolveRoute } from '$app/paths';
</script>

<nav>
  <ul>
    <li><a href="{resolveRoute('/')}">Home</a></li>
    <li><a href="{resolveRoute('/about')}">About</a></li>
    <li><a href="{resolveRoute('/contact')}">Contact</a></li>
    <li><a href="{resolveRoute('/more')}">More</a></li>
  </ul>
</nav>

<style lang="scss">
  nav {
    padding: 1rem 0;
    @media screen and (max-width: 430px) {
      padding: 0;
    }
    ul {
      list-style: none;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      gap: 2rem;
      @media screen and (max-width: 430px) {
        gap: 1.5rem 0.5rem;
        font-size: 0.9rem;
      }
      li {
        a {
          background-color: #123456;
          padding: 0.5rem 1rem;
          text-decoration: none;
          color: #eee;
          border-radius: 10px;
          &:hover {
            background-color: #783489;
          }
        }
      }
    }
  }
</style>
