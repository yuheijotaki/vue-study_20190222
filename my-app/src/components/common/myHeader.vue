<template>
    <header>
      <nav>
        <ul>
          <li><router-link to="/">Top</router-link></li>
          <li><router-link to="/about">About</router-link></li>
        </ul>
      </nav>
    </header>
</template>

<script>
export default {
  name: 'myHeader'
}
</script>

<style lang="scss" scoped>
header {
  nav {
    margin-left: auto;
    ul {
      display: flex;
      list-style: none;
      li {
        font-size: 13px;
        line-height: 1.2;
        margin-right: 20px;
        &:last-child {
          margin-right: 0;
        }
        a {
          color: #ccc;
          text-decoration: none;
          &.is-selected {
            color: #222;
          }
        }
      }
    }
  }
}
</style>
