<script>
  import Button from "../../components/Button";
  import Input from "../../components/Input";
  import RecordTable from "../../components/RecordTable/RecordTable.svelte";
  import Select from "../../components/Select";
  import RecordField from "../../components/RecordField/RecordField.svelte";

  const items = [
    { value: "chocolate", label: "Chocolate", group: "Sweet" },
    { value: "pizza", label: "Pizza", group: "Savory" },
    { value: "cake", label: "Cake", group: "Sweet" },
    { value: "cookies", label: "Cookies", group: "Savory" },
    { value: "ice-cream", label: "Ice Cream", group: "Sweet" }
  ];

  let favouriteFood = undefined;

  function handleSelect(event) {
    favouriteFood = event.detail;
  }

  let records = [
    { label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15" },
    { label: "packetframe.com", type: "AAAA", ttl: 86400, value: "2001:db8::51:3" },
    { label: "packetframe.com", type: "MX", ttl: 86400, value: "10 mail.example.com." },
    { label: "packetframe.com", type: "TXT", ttl: 86400, value: "v=DKwIDAQAB" },
    { label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15", proxied: true},
    { label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15" },
    { label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15" },
    { label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15" },
    { label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15" }
  ];

</script>

<main>
  <a href="https://github.com/packetframe/design">
    https://github.com/packetframe/design
  </a>
  <br>
  <div>
    <Button class="ma-2">Export</Button>
    <Button icon="add" class="ma-2" danger>Export</Button>
    <Button icon="lock" variant="filled" class="ma-2" danger>Export</Button>
    <Button icon="add" disabled class="ma-2">Export</Button>
    <Button icon="add" variant="secondary" class="ma-2">Export</Button>
    <Button variant="flat" icon="lock" class="ma-2" danger>Export</Button>
  </div>
  <Input label="Record" placeholder="Write something here" />
  <Input
    label="Record"
    placeholder="Write something here"
    icon="add"
    error="This is a required field"
  />
  <div style="display: flex; flex-wrap: nowrap;">
    <Input placeholder="Write something here" icon="add" />
    <Select icon="remove" {items} on:select={handleSelect} />
    <Select icon="add" {items} on:select={handleSelect} />
    <Select icon="add" {items} on:select={handleSelect} />
  </div>

  <div style="flex-direction: column; width: 15%">
    <Input label="Username" placeholder="Enter username..." />
    <Input label="Password" placeholder="Enter password..." type="password" />
  </div>

  <div style="max-width: 900px; margin: 0 auto;">
    <RecordField />
    <RecordTable {records} />
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
