<script>
    import RecordTable from "../../../components/RecordTable";
    import RecordField from "../../../components/RecordField";
    import Title from "../../../components/Title";
    import Select from "../../../components/Select";

    let records = [
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "AAAA", ttl: 86400, value: "2001:db8::51:3"},
        {label: "packetframe.com", type: "MX", ttl: 86400, value: "10 mail.example.com."},
        {label: "packetframe.com", type: "TXT", ttl: 86400, value: "v=DKwIDAQAB"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15", proxied: true},
        {label: "packetframe.com", type: "SRV", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
        {label: "packetframe.com", type: "A", ttl: 86400, value: "23.141.0.15"},
    ];

    let zones = ["example.com", "packetframe.com"];
    let zone = zones[0];

</script>

<main>
    <Title>
        <div slot="header">DNS</div>
        <div slot="items">
            <Select bind:selectedValue={zone} items={zones} isSearchable/>
        </div>
    </Title>
    <RecordField/>
    <RecordTable {records}/>
</main>

<style>
    main {
        max-width: 900px;
        margin: 0 auto;
    }
</style>
