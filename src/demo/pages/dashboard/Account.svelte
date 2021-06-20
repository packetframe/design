<script>
    import Input from "../../../components/Input";
    import Card from "../../../components/Card";
    import Button from "../../../components/Button";
</script>

<main>
    <h1>Account</h1>
    <Card title="Change Password">
        <Input style="margin-bottom: 10px" fixErrorHeight={false} label="Password" placeholder="Enter password..." type="password"/>
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
