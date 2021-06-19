<script>
    import Button from "../../components/Button";
    import Input from "../../components/Input";
    import RecordTable from "../../components/RecordTable";
    import Select from "../../components/Select";
    import RecordField from "../../components/RecordField";
    import Navbar from "../../components/Navbar";

    const items = [
        {value: "chocolate", label: "Chocolate", group: "Sweet"},
        {value: "pizza", label: "Pizza", group: "Savory"},
        {value: "cake", label: "Cake", group: "Sweet"},
        {value: "cookies", label: "Cookies", group: "Savory"},
        {value: "ice-cream", label: "Ice Cream", group: "Sweet"}
    ];

    let favouriteFood = undefined;

    function handleSelect(event) {
        favouriteFood = event.detail;
    }

    let records = [
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "AAAA", ttl: 86400, value: "2001:db8::51:3"},
        {label: "packetframe.com", type: "MX", ttl: 86400, value: "10 mail.example.com."},
        {label: "packetframe.com", type: "TXT", ttl: 86400, value: "v=DKwIDAQABeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15", proxied: true},
        {label: "packetframe.com", type: "SRV", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
    ];

</script>

<main>
    <a href="https://github.com/packetframe/design">
        https://github.com/packetframe/design
    </a>
    <br>
    <div>
        <Button class="ma-2">Export</Button>
        <Button class="ma-2" danger icon="add">Export</Button>
        <Button class="ma-2" danger icon="lock" variant="filled">Export</Button>
        <Button class="ma-2" disabled icon="add">Export</Button>
        <Button class="ma-2" icon="add" variant="secondary">Export</Button>
        <Button class="ma-2" danger icon="lock" variant="flat">Export</Button>
    </div>
    <Input label="Record" placeholder="Write something here"/>
    <Input
            error="This is a required field"
            icon="add"
            label="Record"
            placeholder="Write something here"
    />
    <div style="display: flex; flex-wrap: nowrap;">
        <Input icon="add" placeholder="Write something here"/>
        <Select icon="remove" {items} on:select={handleSelect}/>
        <Select icon="add" {items} on:select={handleSelect}/>
        <Select icon="add" {items} on:select={handleSelect}/>
    </div>

    <div style="flex-direction: column; width: 15%">
        <Input label="Username" placeholder="Enter username..."/>
        <Input label="Password" placeholder="Enter password..." type="password"/>
    </div>

    <Navbar/>

    <div style="max-width: 900px; margin: 0 auto;">
        <RecordField/>
        <RecordTable {records}/>
    </div>

    <footer>&copy; Packetframe 2021</footer>
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

  footer {
    margin: 15px;
    color: white;
    text-align: center;
  }
</style>
