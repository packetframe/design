<script>
    import Input from "../../../components/Input";
    import Button from "../../../components/Button";
    import Title from "../../../components/Title";

    let containers = [
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000", "80:80"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
        {hostname: "c1.example.com", image: "packetframe/edge-demo", ports: ["5000:5000"], environment: "FOO=BAR"},
    ]
</script>

<main>
    <Title>
        <div slot="header">Containers</div>
    </Title>
    <div class="pf-containers-inputs">
        <div style="width: 50%; display: flex; flex-direction: column; align-items: stretch;">
            <Input fixErrorHeight={false} label="Hostname"/>
            <Input fixErrorHeight={false} label="Image" placeholder="packetframe/edge-demo"/>
        </div>

        <div class="pf-containers-env">
            <Input
                fixErrorHeight={false}
                inputClasses="pf-containers-textarea"
                label="Environment"
                placeholder="FOO=bar"
                textarea
            />
        </div>
    </div>

    <Button style="margin: 15px 4px" variant="secondary">Add</Button>

    <main>
        <table class="pf-record-table">
            <tr class="pf-record-table__tr">
                {#each ["Hostname", "Image", "Ports", "Environment", ""] as head}
                    <th class="pf-record-table__header">{head}</th>
                {/each}
            </tr>
            <tr class="pf-record-table__spacer"></tr>
            {#each containers as container, i}
                <tr class="pf-record-table__spacer"></tr>
                <tr class="pf-record" class:zebra={i%2 === 0}>
                    <td class="pf-record__label">{container.hostname}</td>
                    <td class="pf-record__type">{container.image}</td>
                    <td class="pf-record__type">{container.ports.join(", ")}</td>
                    <td class="pf-record__type">{container.environment}</td>
                    <td class="pf-record__arrow">
                        <span style="color: #cc0000" class="material-icons-round">delete</span>
                    </td>
                </tr>
            {/each}
        </table>
    </main>
</main>

<style lang="scss">
  main {
    max-width: 900px;
    margin: 0 auto;
    color: white;
  }

  :global(.pf-containers-textarea) {
    height: 100% !important;
  }

  .pf-containers-env {
    width: 50%;

    :global(.pf-input) {
      height: 100% !important;
    }

    :global(.pf-input .pf-input__wrapper) {
      height: calc(100% - 25px);
    }
  }

  .pf-containers-inputs {
    display: flex;
    margin-top: 14px;
  }
</style>
