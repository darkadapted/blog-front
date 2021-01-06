<template>
  <div class="layout">
    <header class="header">
      <strong>
        <g-link to="/" style="color: black;text-decoration: none">
          <g-image alt="Example image" src="../../static/icon.svg" width="100px"/>
        </g-link>
      </strong>
      <nav class="nav">
        <g-link class="nav__link" to="/all-journal" style="color: black;text-decoration: none">Journal</g-link>
        <g-link class="nav__link" to="/contact/" style="color: black;text-decoration: none">Say Hi!</g-link>
      </nav>
    </header>
    <slot/>
    <footer class="footer">
      Copyright © 2021
    </footer>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

.nav__link {
  margin-left: 20px;
}

.footer {
  position: relative;
  bottom: 20px;
  transform: translateY(30px);
  font-size: .8rem;
  padding: 6rem 0;
}
</style>
