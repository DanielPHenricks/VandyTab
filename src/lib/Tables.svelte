<script>
    import DiningHallTable from "./DiningHallTable.svelte";
    import SportsTable from "./SportsTable.svelte";
</script>

<div class="supporting">
    <div class="container">
        <div class="row">
            <div class="col-sm-3">
                <DiningHallTable />
            </div>

            <div class="col-sm-3" />

            <div class="col-sm-3">
                <SportsTable />
            </div>
            <div class="col-sm-3" />
        </div>
    </div>
</div>

<style>
    .container {
        max-width: 56em;
        justify-content: center;
    }
    .supporting {
        text-shadow: 0 2px 3px rgba(0, 0, 0, 0.4);
    }
</style>
