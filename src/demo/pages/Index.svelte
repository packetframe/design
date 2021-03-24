<script>
  import Button from "../../components/Button"
</script>

<main>
  <h1>Packetframe Design Demo</h1>
  <a href="https://github.com/packetframe/design">https://github.com/packetframe/design</a>
  <br>
  <div>
    <Button class="ma-2">Export</Button>
    <Button icon="add" class="ma-2">Export</Button>
    <Button icon="add" variant="filled" class="ma-2">Export</Button>
    <Button icon="add" disabled class="ma-2">Export</Button>
    <Button icon="add" variant="secondary" class="ma-2">Export</Button>
    <Button variant="flat" icon="add" class="ma-2">Export</Button>
  </div>
</main>

<style lang="scss">
  main {
    background-color: #121212;
  }
  h1 {
    color: white;
  }
  div {
    display: flex;
    flex-wrap: wrap;
  }
</style>