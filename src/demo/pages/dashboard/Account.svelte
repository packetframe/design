<script>
    import Input from "../../../components/Input";
    import Card from "../../../components/Card";
    import Button from "../../../components/Button";
    import Title from "../../../components/Title";
</script>

<main>
    <Title>
        <div slot="header">Account</div>
    </Title>
    <Card title="Change Password">
        <Input fixErrorHeight={false} label="Password" placeholder="Enter password..." style="margin-bottom: 10px" type="password"/>
        <Input fixErrorHeight={false} label="Repeat Password" placeholder="Enter password..." type="password"/>
        <Button style="margin-top: 18px" variant="secondary">Save</Button>
    </Card>
</main>

<style>
    main {
        max-width: 900px;
        margin: 0 auto;
        color: white;
    }

    h1 {
        margin-bottom: 10px;
    }
</style>
