<template>
  <div id="footer">
    <div class="hr"></div>
    <div class="container">
      <p>
        <span><strong>&copy; Oskar Olaszczyk, Kamil Skalski</strong>. "Applications in Interpreted Languages"</span>
      </p>
    </div>
  </div>
</template>
<script>
  export default {
    name: "Footer",

  }
</script>

<style scopped>
  #footer {
    margin-bottom: 3em;
  }

  .hr {
    border-bottom: 1px solid #dbdbdb;
    margin: 3em 0;
  }

  #footer p {
    font-size: 15px;
    color: #767676 !important;
  }
</style>
<!--
 <template>
  <footer class="page-footer mdb-color font-small">
    <div class="container-fluid footer-copyright text-center py-3">
      &copy; {{msg}}
    </div>
  </footer>
</template>

<script>
  export default {
    name: "Footer",

    props: {
      msg: String
    },

  }
</script>

<style scoped>

 </style>
 -->
 